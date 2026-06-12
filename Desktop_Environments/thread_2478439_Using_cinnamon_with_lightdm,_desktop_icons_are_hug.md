---
title: "Using cinnamon with lightdm, desktop icons are huge after lockscreen"
date: 2022-08-26
forum: Desktop Environments
---

### Post by guguma2 on 2022-08-26
Hi All,

On Ubuntu 22.04, 2 monitors (laptop + another monitor).
I want to use Cinnamon with Lightdm and slick-greeter on Ubuntu 22.04

I cannot seem to get them to play nice. 

The issue I have is that after the lock screen kicks in when I unlock the screen the icons on the Desktop are magnified to massive sizes.
The icon sizes are OK when I first login though, or they get fixed when I do

```
sudo systemctl restart lightdm
```

I am not sure why? I am keeping both the laptop and the monitor at 1080p

Any ideas?

Edit: People might suggest that I use Linux Mint instead. Unfortunately I cannot, company computer, and only ubuntu is allowed.

Edit: Here is what I did to get cinnamon/lightdm/slick-greeter setup. I might have done something wrong here as well:

```

[COLOR=#1D1C1D][FONT=Slack-Lato]mkdir ~/mint-themes[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]cd ~/mint-themes

[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]sudo apt install cinnamon-desktop-environment
[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]
wget [/FONT][/COLOR][http://packages.linuxmint.com/pool/main/m/mint-x-icons/mint-x-icons_1.6.4_all.deb](http://packages.linuxmint.com/pool/main/m/mint-x-icons/mint-x-icons_1.6.4_all.deb)
[COLOR=#1D1C1D][FONT=Slack-Lato]wget [/FONT][/COLOR][http://packages.linuxmint.com/pool/main/m/mint-y-icons/mint-y-icons_1.6.1_all.deb](http://packages.linuxmint.com/pool/main/m/mint-y-icons/mint-y-icons_1.6.1_all.deb)
[COLOR=#1D1C1D][FONT=Slack-Lato]wget [/FONT][/COLOR][http://packages.linuxmint.com/pool/main/m/mint-themes/mint-themes_2.0.5_all.deb](http://packages.linuxmint.com/pool/main/m/mint-themes/mint-themes_2.0.5_all.deb)
[COLOR=#1D1C1D][FONT=Slack-Lato]
sudo dpkg -i mint-x-icons_1.6.4_all.deb[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]sudo dpkg -i mint-y-icons_1.6.1_all.deb[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]sudo dpkg -i mint-themes_2.0.5_all.deb

[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]sudo apt install lightdm[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]
sudo sed -i 's/Inherits=.*/Inherits=Mint-Y/g' /usr/share/icons/default/index.theme[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]sudo apt install slick-greeter[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]
[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]if test -f "$FILE"; then[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]    echo "found lightdm.conf setting greeter to slick greeter"[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]    
   sudo sed -i 's/greeter-session=.*/greeter-session=slick-greeter/g' $FILE[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]    
   echo "greeter set to slick-greeter at $FILE"[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]    else[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]    echo "Could not find /etc/lightdm/lightdm.conf creating it"[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]    
   sudo touch /etc/lightdm/lightdm.conf[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]    echo -e "[Seat Session]\ngreeter-session=slick-greeter" >> [/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]/etc/lightdm/lightdm.conf[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]    
   echo "greeter set to slick-greeter at /etc/lightdm/lightdm.conf"[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]fi

[/FONT][/COLOR][COLOR=#1D1C1D][FONT=Slack-Lato]echo -e "Please run\nsudo dpkg-reconfigure lightdm and set the manager to lightdm\n then reboot"[/FONT][/COLOR]

```

---

