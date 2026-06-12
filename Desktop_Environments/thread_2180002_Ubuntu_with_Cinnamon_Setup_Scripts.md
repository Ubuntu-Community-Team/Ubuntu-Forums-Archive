---
title: "Ubuntu with Cinnamon Setup Scripts"
date: 2013-10-10
forum: Desktop Environments
---

### Post by maerlyn-broadbent on 2013-10-10
Hi Everyone,

If this is the wrong place for this post please let me know, I'm new to these forums.

I switched to Ubuntu from Windows a week or so ago and so far I'm liking it but I prefer to use the Cinnamon desktop environment over unity. In order to make the initial setup up quick and to learn a bit about bash scripting I thought I would write a bunch of scripts to set everything up for me:

[https://github.com/maerlyngb/UbuntuCinnamonSetupScripts](https://github.com/maerlyngb/UbuntuCinnamonSetupScripts)

Here is a run down of what each file does:

[B]preconf.sh
[/B]prompt for your sudo password
set executable permissions on each of the other scripts
run ci.sh

**ci.sh**
Install Cinnamon and Nemo
Make Nemo the default window manager

[B]conf.sh
[/B]prompt for your sudo password
run rmu.sh
run rms.sh
run t.sh
run i.sh

[B]rmu.sh
[/B]remove unity
remove thunderbird unity extensions
remove compiz
remove nautilus
remove zeitgeist
remove config folders

**rms.sh**
remove gnome-contacts
remove ubuntu one
remove gnome games
remove thunderbird
remove transmission
remove remove empathy
remove videos
remove remove ubuntu landscape
remove remove online profiles
remove remove orca
remove onboard
remove xterm
run apt-get autoremove

**t.sh**
remove all ubuntu online search suggestions
block access to ubuntu search suggestion servers
disable the guest account

**i.sh**
install wine
install wine tricks
install vlc
install gimp
install virtualbox
install deluge
install lightzone

**How to use**
[LIST=1]
[*]open up the terminal and browse to the folder containing the scripts
[*]$ chmod u+x preconf.sh
[*]$ ./preconf.sh
[*]enter your sudo password
[*]when that is finished logout and log back in using Cinnamon
[*]$conf.sh
[*]enter your sudo password
[*]grab a cup of tea and wait for it to finish
[/LIST]

The commands to install cinnamon and remove unity were taken from here:
[http://askubuntu.com/questions/292394/how-to-completely-remove-unity-and-replace-it-with-cinnamon](http://askubuntu.com/questions/292394/how-to-completely-remove-unity-and-replace-it-with-cinnamon)

The commands to remove the online search suggestions were taken from here:
[https://fixubuntu.com/](https://fixubuntu.com/)

Could someone please take a look at these scripts and let me know if anything could be improved/added?

**Thing's I'd like to add but don't know how:**
Is it possible to remove the need to logout of unity and log back into cinnamon?

I would also like to do some other things such as remove the login dots which I've found can be done using this script:
sudo xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-grid false

This doesn't work in the script though since the prompt changes and it won't continue running the rest of the scripts. I've tried to modify the final command like this:

echo "exit" | gsettings set com.canonical.unity-greeter draw-grid false

but this doesn't seem to work.

Thanks in advance for your advice.

I hope these scripts can help someone else setup their own Ubuntu/Cinnamon desktop with minimal stress.

---

### Post by L486XGW on 2013-10-11
You should move your code files to a site like github so its easier for people to browse your code and collaborate code ideas with you and maybe even help provide you with code patches to make it better.

---

### Post by maerlyn-broadbent on 2013-10-11
Thanks for the advice. I'm sure that would work better, I've never done this before so I wasn't sure if anyone would want to collaborate. Judging by the lack of posts on this thread, either no one cares or I've put this in the wrong place. Do you know of a more appropriate place to post this?

Here is the GitHub link to the scripts:
[https://github.com/maerlyngb/UbuntuCinnamonSetupScripts](https://github.com/maerlyngb/UbuntuCinnamonSetupScripts)

Please feel free to download it and make changes. If anyone improves the scripts please let me know so I can incorporate the changes into the main branch.

---

