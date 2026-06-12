---
title: "Post Install Script 8.10 Help"
date: 2008-12-14
forum: General Help
---

### Post by tbuss on 2008-12-14
[SIZE="2"]**Ubuntu 8.10 Post Install Script**[/SIZE]

I'm fairly new to Ubuntu. I have been a user for almost two years; much of that time I have spent using 'the other OS'. I have started to concentrate on Ubuntu once again, and I have to say, this time around I love it. I guess you could say I'm just your average user. I have finally set my system up the way I like it. I have read several HowTo's on how to backup your system, most of which can be found here in the Forums. What I would like to do is automate some of the process of adding repositories, installing software and codecs. I'm aware because of legal reason, Ubuntu cannot be installed with some of this software, and codecs pre-packaged with the distribution. 

**Some of the things I would like to accomplish are as follows:**

Create a script that will run immediatley after a fresh install

[INDENT]- automatically run the Update Manager[/INDENT]

[INDENT]- check for updates and install updates if neccessary[/INDENT]

[INDENT]- 'enables' all the neccessary and/or required repositories (makes changes to the 'sources.lst' as required)[/INDENT]

[INDENT]- or, makes it easy to configure the script to be functional with a new release (When updating from 8.04 to 8.10, etc)[/INDENT] 

[INDENT]- The script will install my software according to what is in the file from running: ```
dpkg --get-selections > installed-software
```
[/INDENT]

I guess, in a nutshell, I need help in creating a script that will automate the process of re-installing my sytem software, codecs and keeping my sources.list intact. I have never used a programming language in my life, but from doing some reading it appears I can achieve this goal by creating a bash script. If anyone has any advice or suggestions I would greatly appreciate it. Any constructive critism is welcome as well :)

**Below is my 'newbie" attempt at outlining how I think the script should run.**


[SIZE="2"]**Installing Updates after initial install:**[/SIZE]

[I]Execute Post-Install-Script
[/I]
- Post-Install-Script runs the following:
[INDENT]- Checks to see if Post-Install-Script has been previously executed[/INDENT]
[INDENT][INDENT]- If no[/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- Checks to see if the Update Manager has been execute[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]- If no[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Open Update Manager[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Refresh list[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Install Updates[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Prompt for Password[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

[INDENT][INDENT][INDENT][INDENT][INDENT]- Enter Password[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

[INDENT][INDENT][INDENT][INDENT][INDENT]- Update installation continues[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Update Manager closes after updates are installed[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]- If Kernel was updated[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]- Then system restarts[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]- After restart Execute Post-Install-Script[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]- If no restart required, continue with software installation[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT]- Checks if software in Post-Install-Script is installed on system[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]- If yes[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Exit[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]- If no[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Continue with software installation[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT]- If yes[/INDENT][/INDENT] 
[INDENT][INDENT][INDENT]- Check to see if Update manager has any updates[/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]- If yes[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Run Update Manager[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT]- If no[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT][INDENT][INDENT][INDENT][INDENT]- Continue with software installation [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT]- Continue with software installation[/INDENT]
  

[SIZE="2"]**This is the part where the script will automatically configure the sources.lst**[/SIZE]

[SIZE="2"]**Configure Additional Repositories**[/SIZE]

**- edit /etc/apt/sources.list**

*- enable the intrepid partner repository*
```
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
```

*- enable the Medibuntu repository*
```
[SIZE="2"]sudo wget [http://www.medibuntu.org/sources.list.d /intrepid.list](http://www.medibuntu.org/sources.list.d /intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update[/SIZE]
```

*- enable all repositories (including Universe and Multiverse repositories)*
```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update
```

*- enable OpenOffice 3*
```
[SIZE="2"]echo 'deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main' >> 
/etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update[/SIZE]
```

[SIZE="2"]**Install Additional Software**[/SIZE]

*- Enable Synaptic to install the additional applications (User preference)*
```
sudo update-apt-xapian-index
```

*- Software Install*
[INDENT]- Software installed from 'installed-software' file [/INDENT]
 ```
dpkg --get-selections > installed-software
```

---

