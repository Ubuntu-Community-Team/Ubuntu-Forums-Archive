---
title: "SDLmame, wahcade working - now i just need to hide ubuntu"
date: 2007-08-31
forum: Gaming &amp; Leisure
---

### Post by mahalos on 2007-08-31
Hey,

I have SDLmame running sweet with Wahcade as a frontend.

 Now all i need to figure out is how to have Ubuntu boot directly into Wahcade. I don't mind seeing the bootup logo cause i can change that to something more Arcade-like, but from there i'd rather not see anything until wahcade starts.  Does anyone know how to do something along these lines??

Any help appreciated

Carl

---

### Post by KingHanco on 2007-08-31
Ask these guys over here at... [http://www.mameworld.info/ubbthreads/postlist.php?Cat=&Board=mamechat](http://www.mameworld.info/ubbthreads/postlist.php?Cat=&Board=mamechat)

---

### Post by mahalos on 2007-08-31
> **KingHanco said:**
> Ask these guys over here at... [http://www.mameworld.info/ubbthreads/postlist.php?Cat=&Board=mamechat](http://www.mameworld.info/ubbthreads/postlist.php?Cat=&Board=mamechat)

Thanks for the tip. I've put a post up there, but I spent a lot of time on those forums back in my Windows days, and i don't think many of them are linux savvy.........but i guess we'll soon find out.

---

### Post by Dirkomatic on 2007-08-31
I've got the same setup.  The key is turning off the usplash logo on boot.  See if you can figure it out from this thread:

[http://ubuntuforums.org/showthread.php?t=192675](http://ubuntuforums.org/showthread.php?t=192675)

If I remember, I'll post my settings this weekend.

---

### Post by mahalos on 2007-08-31
Thanks Dirkomatic,

thanks for your input I had a look at the thread and it seemed more about removing/prettying up the boot process.  I've been using a nice Gui app called Startup Manager to handle this and it works great.

However i don't mind the Usplash as i fancy creating an arcade style one to replace the ubuntu one. What i really want to try and figure out is how to stop the GDM from starting and just load wahcade.  I've got wahcade setup as a startup program, but you have to see the desktop etc before it loads, i quite fancy nice clean boot straight into whacade

---

### Post by ddr on 2007-09-05
Can you tell me how you got WahCade running with sdlmame?  What version of each are you using?  I am trying 0.115 of sdlmame and 0.22 of WahCade and WahCade cannot read my mameinfo.xml file.

Thanks,
Dan

---

### Post by ddr on 2007-09-05
Here is how I setup Fedora 7 to boot directly into Wah!Cade:

0) Setup Fedora to boot without GDM or KDM (in fact, I do not have Gnome or KDE installed)
1) Ran 'startx' as user mame to get X running
2) Edited /etc/X11/xinit/Xclients to start Wah!Cade and nothing else:

[INDENT]If you look in this file you might see the section where twm is started as a last resort.  I edited this section commenting out the clock, Xterm and twm, and adding Wah!Cade:

```
# Argh! Nothing good is installed. Fall back to twm
{
    # gosh, neither fvwm95 nor fvwm2 is available;
    # fall back to failsafe settings
    [ -x /usr/bin/xsetroot ] && /usr/bin/xsetroot -solid '#222E45'

    #if [ -x /usr/bin/xclock ] ; then
        #/usr/bin/xclock -geometry 100x100-5+5 &
    #elif [ -x /usr/bin/xclock ] ; then
        #/usr/bin/xclock -geometry 100x100-5+5 &
    #fi
    #if [ -x /usr/bin/xterm ] ; then
        #/usr/bin/xterm -geometry 80x50-50+150 &
    #fi

[COLOR="Red"]    if [ -x /usr/games/wahcade ] ; then
        /usr/games/wahcade --full-screen
    fi[/COLOR]

    #if [ -x /usr/bin/firefox -a -f /usr/share/doc/HTML/index.html ]; then
        #/usr/bin/firefox /usr/share/doc/HTML/index.html &
    #fi
    #if [ -x /usr/bin/twm ] ; then
        #exec /usr/bin/twm
    #fi
}
```

[/INDENT]
3) Exited X by hitting CTRL-ALT-Backspace

4) Started X again by typing 'startx'  This time I get just WahCade, with no window manager.  To get back to the command prompt I hit escape to exit WahCade and X shuts down

5) Setup Fedora to log user mame in automatically on tty1 at boot by editing /etc/inittab and replacing this line:

[INDENT]1:2345:respawn:/sbin/mingetty tty1[/INDENT]

with this one:

[INDENT]1:3:respawn:/sbin/mingetty --autologin mame tty1[/INDENT]

7) Test the inittab change by rebooting, sure enough mame got logged in automatically

8) Setup mame's ~/.bash_profile to start X at login if the login is on tty1 by adding this to ~/.bash_profile:

```
# start X if we are logged in on tty1:
case "`tty`" in  
    /dev/tty1)
                startx && exit
                ;;  
esac
```

9) Tested to see that X starts automagically by logging out from tty1, there is no need to reboot as the 'respawn' instruction in inittab automatically logs mame back in whenever that user logs out from tty1.  This has the side effect of restarting WahCade if the player hits escape and exits completely

Let me know if this does not work on Ubuntu, I can load Ubuntu and work out the details if needed.

Dan

---

