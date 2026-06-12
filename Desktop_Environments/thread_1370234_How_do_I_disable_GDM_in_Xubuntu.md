---
title: "How do I disable GDM in Xubuntu"
date: 2010-01-02
forum: Desktop Environments
---

### Post by mike_yung on 2010-01-02
I've been tinkering with Linux for over a decade but am brand new to Ubuntu & their forums.  If this thread fits better in another Forum please let me know.  I'm here to learn.

How does one disable GDM in Xubuntu [COLOR=Red]9.04[/COLOR][FONT=Comic Sans MS][SIZE=2][COLOR=SeaGreen] (correction 9.10)[/COLOR][/SIZE][/FONT] ?  On startup I'd like to be presented with a login prompt on tty1 so the logged in user can bring up Xfce with startx if it's needed.

I thought this would be done by changing the default runlevel from five to three.  I was quite surprised to find Ubuntu default's to two with many many services running.  I was also quite surprised to find no link to GDM in etc/rc2.d when I tried to disable GDM there.

:confused:

---

### Post by Warren Watts on 2010-01-02
```
sudo apt-get remove gdm
```

that will remove GDM and you will boot to a tty login

---

### Post by mike_yung on 2010-01-02
Thanks for the quick response.  This didn't work the way we expected.  Instead of a login prompt on the console, I was surprised to see an error about a Xfce not being able to find a font & a dialog box offering the choice of Xfce in low graphics mode or a console.

I found with either option my screen blanked complaining of out of range signals.  I was able to back to square one by putting gdm back in via ssh.

Taking the display manager out sounds a little extreme to me.  It may be overkill, or may only seem that way to me due to my perspective.  I'd been using Gentoo & Debian before.  Both of these distro's use /etc/inittab & allow the display manager easily be be disabled.

If you are sure removing gdm altogether is the best approach I'll give it another try & make notes of the error messages.

Perhaps I should have mentioned, I'm not exactly running Xubuntu.  I installed the Ubuntu server 9.10 first then put in *xubuntu*-*desktop package*.

---

### Post by hariks0 on 2010-01-02
Just press Ctrl+Alt+F1

---

### Post by mike_yung on 2010-01-02
> **hariks0 said:**
> Just press Ctrl+Alt+F1

Pressing Ctrl+Alt+F1 switches to tty1.  That's not what I want.  

I want to set-up my system so one is presented with a login prompt on tty1 on startup.  If Xfce is needed it can be started from the shell with startx.

---

### Post by mike_yung on 2010-01-05
Someone had the same question a couple of days later & recieved a completely different answer.  [http://ubuntuforums.org/showthread.php?t=1305659](http://ubuntuforums.org/showthread.php?t=1305659)

According to my understanding of that advice there are two options.

[LIST=1]
[*]One is to edit /etc/init/gdm.conf adding a line telling gdm to start on run level 3.
[*]The other is to edit /etc/default/grub changing GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"
[/LIST]
That leaves me with four follow up questions.

[LIST=1]
[*]Am I interpreting [http://ubuntuforums.org/showthread.php?t=1305659](http://ubuntuforums.org/showthread.php?t=1305659) correctly?
[*]What advantage does upstart have over  System-V style init scripts?
[*]Why have the development team neglected to mention their major off-road excursion into upstart in the 9.10 Ubuntu Server Guide?
[*]Is this normal for Ubuntu?  When I start poking under the hood am I to expect more poorly documented unsupportable wackiness?
[/LIST]

---

### Post by rippin on 2010-01-06
> **mike_yung said:**
> Someone had the same question a couple of days later & recieved a completely different answer.  [http://ubuntuforums.org/showthread.php?t=1305659](http://ubuntuforums.org/showthread.php?t=1305659)

According to my understanding of that advice there are two options.

[LIST=1]
[*]One is to edit /etc/init/gdm.conf adding a line telling gdm to start on run level 3.
[*]The other is to edit /etc/default/grub changing GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"
[/LIST]
<snip>


Hate not to be able to answer you directly for 9.10 as I use 9.04. I see no easy clean up for this want you first mentioned. I suggest, lacking a better guide, a more thorough plan of action and re-installing your system - if practicable - as a minimal install; I have so done. We have no login screen such as GDM and each user has a specially written script to login them in and out as suits them.

Examples:
.bashrc
<snipped>

alias xf='startx > /dev/null 2>&1'
--------------------------------------

.bash_profile 
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

startx
exit

------------------------

.bash_logout 
# ~/.bash_logout: executed by bash(1) when login shell exits.

# when leaving the console clear the screen to increase privacy
# and history for brevity, plus .xsession-errors as it is not
# being automatically updated between login/out.

echo -n > .bash_history
echo -n > .xsession-errors

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi

---

### Post by gsmanners on 2010-01-06
> **mike_yung said:**
> 
[LIST=1]
...
[*]What advantage does upstart have over  System-V style init scripts?
[*]Why have the development team neglected to mention their major off-road excursion into upstart in the 9.10 Ubuntu Server Guide?
[*]Is this normal for Ubuntu?  When I start poking under the hood am I to expect more poorly documented unsupportable wackiness?
[/LIST]

Upstart is a custom init daemon designed to handle its job more flexibly than the old init. It isn't paraded around in the documentation, but it is documented (man init). See also [http://www.linux.com/archive/feature/125977?theme=print](http://www.linux.com/archive/feature/125977?theme=print)

I have no idea who wrote the Ubuntu Server Guide. It probably does need a refresh and to mention things like this.

Yes, unfortunately Ubuntu developers do tend to leap before they look. See the recent decisions regard The GIMP for example.

---

### Post by mike_yung on 2010-01-24
Solved

> **mike_yung said:**
> edit /etc/init/gdm.conf adding a line telling gdm to start on run level 3.

---

