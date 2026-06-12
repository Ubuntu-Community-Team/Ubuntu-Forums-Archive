---
title: "Switching Keyboards"
date: 2010-10-28
forum: Desktop Environments
---

### Post by Paul A C on 2010-10-28
I am wanting to be able to switch between English (UK) and Finnish (FI) keybords in Lubuntu.

I tried the command setxkbmap -option grp:ctrl_shift_toggle uk.fi 

but got the response error loading keyboard file.  I tried adding -config to \usr\x11\kbr but to no avail.

Any idea how to install and switch keyboard layouts?

---

### Post by cavalier911 on 2010-10-29
I prefer alt_shift as you can do the keys in either order, ctrl_shift only toggled if I start with the Shift key.
Test:
```
setxkbmap -layout "gb,fi" \ -option "grp:alt_shift_toggle"
```

to make it persist in X
Edit /etc/X11/xorg.conf

```
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
Option      "XkbLayout" "gb,fi"
Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection
```

To see all the keymaps and keyboards:
```
less /usr/share/X11/xkb/rules/xorg.lst
```

---

### Post by Paul A C on 2010-10-29
Cavalier 911, thanks for your reply.  The code you suggest works a treat.  Just one problem, I have no xorg.conf in /etx/x11 in Lubuntu, I have Xsession.options, and Xwrapper.config, but I don't think this is what I want.

Should I create a X11.conf? Or is there a different conf files used by Lubuntu?


Also ideally I would like this set for just one user, and better still have one keyboard on one desktop and the other keyboard on the other desktop.  

thanks

P

---

### Post by cavalier911 on 2010-10-30
The xorg.conf would make the configuration global and kick in as soon as Xserver starts.No xorg.conf by default,but it's easy to boot into rescue mode and auto-generate one with the X -configure command.

This change will not take effect until the user is logged on to the desktop,after the graphical Login.
Login to user's account you want to configure.
_**No**_ sudo with any of these commands,files and folder must be owned by the local user. 
Add this script to the bottom of .bashrc to add local user bin to $PATH
```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```
```
mkdir ~/bin
```
Logout and back in,verify local users bin is in $PATH:
```
echo $PATH
```
This should include /home/localusername/bin
Make the script:
```
touch ~/bin/swichkbmap
```
```
nano ~/bin/swichkbmap
```
Add this:
```
setxkbmap -layout "gb,fi" \ -option "grp:alt_shift_toggle"
```
Make it executable:
```
chmod 744 ~/bin/swichkbmap
```
Reboot,log back in to that account.
Test the script:
```
swichkbmap
```
Verify keyboard change is made.
Make the autostart file if necessary with the touch command.
```
nano ~/.config/lxsession/Lubuntu/autostart
```
Add **@swichkbmap**
Shutdown,reboot,login test keyboard.

> one keyboard on one desktop and the other keyboard on the other desktop
I googled "virtual desktop different keymap" and came up with nothing.

---

### Post by Paul A C on 2010-10-31
[cavalier911]("http://ubuntuforums.org/member.php?u=847951")
The xorg.conf  would make the configuration global and kick in as soon as Xserver  starts.No xorg.conf by default,but it's easy to boot into rescue mode  and auto-generate one with the X -configure command.

Having trouble creating the xorg.conf file.  

I tried stopping LXDM
> sudo /etc/init.d/lxdm stop
which stopped X OK,
But then when I tried to run 
> X -configure
I was asked to login.  My username was not accepted, so I guess root was wanted.  Do I need to enable root user?  A bit of a pain.

I think if I can create XConf I should be able to get this to work.

I need step by step instuctions to create this file by the looks of it, certainly anything as 'easy' as X -configure doesn't work!

---

### Post by cavalier911 on 2010-11-02
See this: [http://ubuntuforums.org/showthread.php?t=1544285](http://ubuntuforums.org/showthread.php?t=1544285)
          Thread #2
          Begin with:
First we have to boot into recovery mode from grub menu, hold shift if menu is hidden.
After you finish booting to the recovery menu choose last selection root.
Scroll down almost to the bottom of xorg.conf

Skip the Add whats in bold use this instead:
```
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
Option      "XkbLayout" "gb,fi"
Option      "XkbOptions" "grp:alt_shift_toggle"
EndSection
```
 
Continue to end.

---

### Post by Paul A C on 2010-11-04
Thanks everyone for your help, and I am sure I will want to know how to make xorg.conf sometime, but I found a much simpler way of achieving what I wanted. Being able to switch keyboards; what I did was:- edit 
etc\xdg\lxsessionzlubuntu\autorun, add:-
```
setxkbmap -layout “gb,fi,it,gb”
 fbxkb

```Note that I put gb in twice, that is because of a Bug in fbxkb whereby the first layout is dispalyed as ??.  (Usually reported as US displays as ??, but in fact it is the first layout no matter what you make it that does not work).  There may be a patch for that, I have not tried it yet.

Easy?  The biggest problem was to work out which of the myraid of files to put this in.

---

