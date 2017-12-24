+++
title = "New Computer Install"
description = "Programmatic steps to setup up your new OS X for Software Development"
date = "2017-04-10T16:43:08+01:00"
draft = false
weight = 200
bref="Developers rarely setup their OS X environments from a fresh installation. And when they do, they usually don't keep track of what exactly was installed nor the steps they did to install the software. Here are programmatic steps to setup your new OS X for Software Development"
toc = true
+++

<h3 class="section-head" id="h-homebrew"><a href="#h-homebrew">Homebrew</a></h3>

Open the Terminal.app and copy, paste & run these commands below:

<pre class="code">
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap caskroom/versions
brew install bash go tree git zsh node
brew cask install slack docker kitematic macdown caffeine licecap etcher royal-tsx divvy sublime-text visual-studio-code-insiders google-chrome
</pre>


<h3 class="section-head" id="h-zsh"><a href="#h-zsh">Zsh</a></h3>

Install Zsh:

<pre class="code">
echo '/usr/local/bin/zsh' | sudo tee -a /etc/shells 
chsh -s /usr/local/bin/zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
</pre>


<h3 class="section-head" id="h-golang"><a href="#h-golang">Golang</a></h3>

Install Golang Libraries and setup environment:

<pre class="code">
echo "export PATH=\$PATH:$HOME/go/bin" >> ~/.zshrc
echo "export GOPATH=\$HOME/go" >> ~/.zshrc
go get -u -v github.com/kardianos/govendor
go get -u -v github.com/rogpeppe/godef
go get -u -v github.com/golang/lint/golint
go get -u -v github.com/tpng/gopkgs
go get -u -v github.com/lukehoban/go-outline
go get -u -v github.com/nsf/gocode
go get -u -v golang.org/x/tools/cmd/goimports
go get -u -v github.com/uudashr/gopkgs/cmd/gopkgs
go get -u -v github.com/ramya-rao-a/go-outline
go get -u -v github.com/acroca/go-symbols
go get -u -v golang.org/x/tools/cmd/guru
go get -u -v golang.org/x/tools/cmd/gorename
go get -u -v github.com/fatih/gomodifytags
go get -u -v github.com/haya14busa/goplay/cmd/goplay
go get -u -v github.com/josharian/impl
go get -u -v github.com/cweill/gotests/...
</pre>

<h3 class="section-head" id="h-vs-code"><a href="#h-vs-code">Visual Studio Code</a></h3>

Install Visual Studio Code Libraries and setup environment:

<pre class="code">
echo "PeterJausovec.vscode-docker \
Tyriar.sort-lines \
bungcip.better-toml \
dbaeumer.vscode-eslint \
donjayamanne.python \
lukehoban.Go \
mauve.terraform \
zxh404.vscode-proto3" | tr " " "\n" | while read lib; do "/Applications/Visual Studio Code - Insiders.app//Contents/Resources/app/bin/code" --install-extension $lib; done

echo '{"go.formatTool":"goimports","workbench.iconTheme":null,"terminal.integrated.shell.osx":"/usr/local/bin/zsh","workbench.welcome.enabled":false,"editor.cursorBlinking":"solid","editor.tabSize":2,"editor.rulers":[80,100,120]}' | python -m json.tool > "$HOME/Library/Application Support/Code - Insiders/User/settings.json"
</pre>

