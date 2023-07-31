# WSL Ubuntu Environment configuration

## Enable systemctl boot

In ubuntu enviroment, create a wsl file configuration.

```bash
sudo -e /etc/wsl.conf
```

In the file, set the lines:

```txt
[boot]
systemd=true
```
Then, restart ubuntu in powershell terminal.

```bash
wsl --shutdown
```

# Add branch in terminal line

Then run the command bellow:

```bash
echo "
# add branch in terminal line
if [ -e /usr/bin/git ]; then
	parse_git_branch() {
		git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
	}
	export PS1=\"\[\033[1;32m\]\u@\h:\[\033[1;34m\]\w\[\033[33m\]\\\$(parse_git_branch)\[\033[00m\]$ \"
fi
" >> /home/$USER/.bashrc
```

After add the lines above, refresh the bash terminal with the command:

```bash
source /home/$USER/.bashrc
```

# Install Docker

You can follow the install guide in [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/).

To execute docker without the command sudo, run the commands:

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

# Install NVM - Node Version Manager

You can follow the install guide in [nvm install](https://github.com/nvm-sh/nvm#installing-and-updating).


