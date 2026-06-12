---
title: "sh script to install, uninstall and customise desktop"
date: 2008-12-14
forum: General Help
---

### Post by Berduchwal on 2008-12-14
Hi
After Ubuntu was installed I always install some application, uninstall other application change my language files I managed to created sh file that does this in one go with no user interference:

```

cp /etc/apt/sources.list /etc/apt/sources.list.backup
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
echo 'deb http://ppa.launchpad.net/patryk-prezu/ubuntu intrepid main' >> /etc/apt/sources.list.d/marcin.sources.list
echo 'deb http://download.skype.com/linux/repos/debian/ stable non-free' >> /etc/apt/sources.list.d/marcin.sources.list

echo Sources updated, system updated starts

apt-get update
apt-get upgrade -f -y
apt-get autoremove -y

echo System updated removal and installation of packages starts

apt-get remove evolution pidgin totem rhythmbox gnome-games ekiga totem-mozilla -y
apt-get install thunderbird planner dia kmymoney2 vlc amarok python-dev librsync-dev -y
apt-get install mozilla-plugin-gnash mozilla-plugin-vlc firefox-showcase -y
apt-get install kadu skype -y --force-yes


```

This is just part of the script which is much longer but it is generally looking like this.

Apart from installing and uninstalling I also want to do other things.

1) set default applications
so far I can only set VLC as my default player using:
```

mkdir ~/.local/share/applications
cp /usr/share/applications/vlc.desktop ~/.local/share/applications/vlc-dvd.desktop
cat ~/.local/share/applications/vlc-dvd.desktop | sed 's/Exec=vlc %U/Exec=vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %f/g' > ~/.local/share/applications/vlc-dvd.desktop
cat ~/.local/share/applications/vlc-dvd.desktop | sed 's/Exec=vlc %f/Exec=vlc --vout-filter deinterlace --deinterlace-mode blend --volume 512 --fullscreen %f/g' > ~/.local/share/applications/vlc-dvd.desktop

```

I would also like to set Thunderbird for email and Amarok for music.
Can some one guide me to some reading regarding how to do this?

2) I would also like to remove some obsolete elements of the menu like, totem short cut is still there although application have been removed the same with Evolution.

Can some one tell me how to do this via terminal?

3) Final thing I would like to do is to record terminal session while script is running. I normally use **scrip** for that but it halts execution of my script :( so is of no use.

Are there any alternatives to script that can be triggered from command line and will not halt executions of sh file? If the answer is yes then could you please point me to man page or something else where I can read about it?

4) Adding wireless points passwords and SSID? Is this possible at all? Can I do this from the terminal? Can you please suggest reading about this?


I am sure there will be more questions once I get into more advanced stuff but so far those are the only issues. Thank you in advance!

---

### Post by Berduchwal on 2008-12-23
Another issue I have recently experienced:

The completed script works on my PC but does not work then transfered to the other PC simple commands like:
```
apt-get update 
```
throw errors!

Any suggestions?

---

