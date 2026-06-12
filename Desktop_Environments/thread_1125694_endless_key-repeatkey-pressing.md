---
title: "endless key-repeat/key-pressing"
date: 2009-04-14
forum: Desktop Environments
---

### Post by nazarener on 2009-04-14
Hi,

i am running openbox on my server, which is running x11vnc.
occasionally it happens when typing, that the computer just keeps repeating one key forever (for example just prints aaaaaaaaaaaaaaaaaaaaa.... and so) although i dont press that button anymore. Actually key-repeat doesnt work at all (holding the a-button just gives one single a).

when i close the vnc client, the server is still sending the letter and doesnt stop until i restart the xserver.

---

### Post by tkelito on 2009-04-14
I used to have a similar problem using VNC over my network, it was partly solved by a faulty router causing the network to crawl and changing the compression method.  Also if you use encryption and it is a local network I would disable it (unless it is an open wireless network or you have a reason to need to encrypt locally).

I use RealVNC and have no issues.  Our network is a mix 'n match between Windows XP, Vista, 7, Ubuntu, Redhat, and Server 2003.  And all function no problem but it took some tweaking.

-tkelito

---

### Post by krunge on 2009-04-14
> **nazarener said:**
> 
i am running openbox on my server, which is running x11vnc.
occasionally it happens when typing, that the computer just keeps repeating one key forever (for example just prints aaaaaaaaaaaaaaaaaaaaa.... and so) although i dont press that button anymore. Actually key-repeat doesnt work at all (holding the a-button just gives one single a).

when i close the vnc client, the server is still sending the letter and doesnt stop until i restart the xserver.

What happens if, at the actual keyboard, you press and release "a" once?  Doesn't that release the key?  I believe releasing the stuck key could be done by tapping it through VNC as well.

[http://www.karlrunge.com/x11vnc/faq.html#faq-repeated-keys](http://www.karlrunge.com/x11vnc/faq.html#faq-repeated-keys)

[http://www.karlrunge.com/x11vnc/faq.html#faq-repeated-keys-still](http://www.karlrunge.com/x11vnc/faq.html#faq-repeated-keys-still)

[http://www.karlrunge.com/x11vnc/faq.html#faq-mod-stuck-down](http://www.karlrunge.com/x11vnc/faq.html#faq-mod-stuck-down)

---

### Post by nazarener on 2009-04-15
hi, thanks for your replies.
tapping 'a' repeatly afterwards doesnt help.
somehow i am not sure that this is an repeat rate issue. when for example spamming aaaaaaaaaaaaaaaaaa i can press other buttons like b to get aaaaaaaaabaaaaaaaaa.
furthermore even after 8 hours, during which the vnc client was shut down, the computer still keeps printing a's.
i also tried "xset r off", which didnt help
also i never get double or triple keystrokes when typing.

---

### Post by krunge on 2009-04-15
> **nazarener said:**
> 
tapping 'a' repeatly afterwards doesnt help.
somehow i am not sure that this is an repeat rate issue. when for example spamming aaaaaaaaaaaaaaaaaa i can press other buttons like b to get aaaaaaaaabaaaaaaaaa.
furthermore even after 8 hours, during which the vnc client was shut down, the computer still keeps printing a's.
i also tried "xset r off", which didnt help
also i never get double or triple keystrokes when typing.

I'm not sure what is happening then.  Try running x11vnc with one or two '-dk' on its cmdline to get debugging output for every keystroke. This is to try to determine if x11vnc is actively injecting the a's or not.

You might want to also try the xev(1) command to get more info. Using its '-id' option you can attach it to the window getting all of the a's (see xwininfo(1)).  Or maybe the xev window starts getting them as soon it has focus. Report back what you find.

---

### Post by nazarener on 2009-04-15
i used the xev window, but i am unsure how to understand it.
here is the link to a screenshot (copy paste doesnt work if my computer is spamming backspace's)
[[IMG]http://img171.imageshack.us/img171/1953/screenshothwc.th.png[/IMG]](http://img171.imageshack.us/my.php?image=screenshothwc.png)

looks exactly like a normal keypress. and as i said before, it keeps spamming it although the VNC client is disconnected and no keyboard is plugged in into the server.

---

### Post by krunge on 2009-04-15
> **nazarener said:**
> 
looks exactly like a normal keypress. and as i said before, it keeps spamming it although the VNC client is disconnected and no keyboard is plugged in into the server.

Since the repeating keystroke was applied to the xev window that could be good info.

If you look at the xev output you see the 'state 0x10' output.  For my computers that usually means NumLock is latched.  It probably means the same for you, but you could double check by running "xmodmap -pm".

Is having NumLock pressed/latch normal for your setup?  Does unlatching it make a difference?  Sometimes having ScrollLock or NumLock latched for me messes up my X server (but not with keyrepeating, just that the modifiers state isn't recognized.)

What sort of output do you get from x11vnc with '-dk -dk' debugging output  option?

Also post "xset -q" output.

---

### Post by krunge on 2009-04-15
> **nazarener said:**
> although the VNC client is disconnected and no keyboard is plugged in into the server.

I missed this part.  Does the problem happen when the machine has a keyboard plugged in?

---

### Post by nazarener on 2009-04-20
hi, thanks for your replies, i was quite busy recently.
when i plug a keyboard in the keypress still goes on, but as soon as i start typing, it stops. i dont know yet if the key-repeating also happens, when a keyboard is plugged in permantly.

---

### Post by krunge on 2009-04-25
Which OS/distro are you running and the version number?

---

### Post by NoThanksM$ on 2009-04-28
This exact same problem is happening to me.  I was running the 32 bit version of Ubuntu (actually Mythbuntu) 8.10 and was fine with that and all previous versions, but have had this problem ever since I upgraded to Jaunty 9.04. Almost everything described above fits my scenario, except I believe when I close down the VNC client the key repeating stops.  If I open it again, it picks up where it left off.  Oh, and I do have a keyboard connected to the host computer.  Other than that, my situation is exactly the same as above.

---

### Post by krunge on 2009-04-28
What are the Xorg version numbers for your 8.10 and 9.04 ubuntu installations?  "/usr/bin/Xorg -version" might work too.  I feel this is bug in Xorg...

I assume you used x11vnc version 0.9.3 in both cases, no?

---

### Post by NoThanksM$ on 2009-04-28
Not sure what my Xorg version in Intrepid was, I just whatever was the default which from Google searches is turning up as 7.4  However, when I run the command you provided on my current installation (Jaunty), I get the following:

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu

Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.

Which obviously doesn't have version numbers that look like they'd come after 7.4.

I was using the a pre-final version of 0.9.7 x11vnc in Intrepid, then for the first day or two of Jaunty was using 0.9.3 (before I realized the OS upgrade downgraded x11vnc) and today was using the final 0.9.7 x11vnc.  So it happened in both 0.9.3 and 0.9.7 for me.

Also, one correction to what I stated above:  when I got home today, the key repeat thing was still happening despite my x11vnc session being closed.  One key press on the physical keyboard stopped it, though.

---

### Post by krunge on 2009-04-29
> **NoThanksM$ said:**
> 
Also, one correction to what I stated above:  when I got home today, the key repeat thing was still happening despite my x11vnc session being closed.  One key press on the physical keyboard stopped it, though.

Some x11vnc options to try as separate experiments:
```

-repeat
-xkb
-noxkb

```

And for all cases you should add "-dk" to get debugging output printed for each key event.  Save the output in a file (-o filename) for follow-on questions, etc.

---

### Post by brianmcb on 2009-04-30
I had the same problem after upgrading.  To fix it, I use "-norepeat -1" when running x11vnc.  The -1 tells it to keep resetting to norepeat an infinite number of times.

---

### Post by NoThanksM$ on 2009-04-30
Thanks, Brian, I'll give that a try.

Karl, I haven't responded yet because for the past couple of days I've been struggling with horrible VNC performance issues which I've yet to resolve.  It doesn't appear to be an overall problem with my connection, but there's no reason for me to think it's x11vnc either so I've got to figure that problem out first before working on this one further.

---

### Post by bj0 on 2009-04-30
I've been getting this problem the last couple of days.  I use VNC (through openVPN) a lot to connect to my home PC from my laptop.  

I never had this problem with 8.10, but after a fresh install of 9.04, it seems to happen almost every time I am using vnc.  I'm using x11vnc (because vino doesn't work with compiz), and I've gotten the behavior in both vinarge and xvnc4server.

Once it started repeating a's, I tried disconnecting, pkilling x11vnc and restarting, and xset r off.  Nothing stopped the key repeat spam, and since I'm not currently at home I can't hit the keyboard.

I'll try some of the options suggested when I get a chance, but since I can't stop the spam right now, the doesn't seem to be a point until I get home...

---

### Post by bj0 on 2009-04-30
Ok I have an update.  I was able to get control of my keyboard by using the **-grabkbd** option.  This made it so I could type normally and I didn't even need to xset r off.

The strange thing is, it seems my keyboard is still stuck sending the 'a' signal, because as soon as I disconnect my vnc session (and keyboard is no longer 'grabbed'), the a's start spamming again.  I'm guessing If I used this from the start I wouldn't have started the spam in the first place, but who knows?  This is also not a good solution if you want to share the keyboard with someone at the computer.


Another side effect of -grabkbd which doesn't make any sence to me is that I can no longer see any menus.  I click on any menus (window menus, gnome menu, popup-menus) and they don't come up.  The menu is highlighted like it was selected, but nothing appears and clicking where the menu 'would be' just selects what is underneath.

Strange.

---

### Post by krunge on 2009-04-30
> **NoThanksM$ said:**
> I haven't responded yet because for the past couple of days I've been struggling with horrible VNC performance issues which I've yet to resolve.  It doesn't appear to be an overall problem with my connection, but there's no reason for me to think it's x11vnc either so I've got to figure that problem out first before working on this one further.

Maybe try the x11vnc option "-noxdamage"?  It's not clear Xorg will ever fix that bug...

Search these forums for "noxdamage" for more information and also here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-beryl](http://www.karlrunge.com/x11vnc/faq.html#faq-beryl)

---

### Post by bj0 on 2009-05-01
> **krunge said:**
> Maybe try the x11vnc option "-noxdamage"?  It's not clear Xorg will ever fix that bug...

Search these forums for "noxdamage" for more information and also here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-beryl](http://www.karlrunge.com/x11vnc/faq.html#faq-beryl)

I use -noxdamage because x11vnc and compiz don't work together without it, but I still get the key-repeat problem.

I got it with -norepeat -1  too.

---

### Post by kszys on 2009-05-04
I have the same behaviour since upgraded from Intrepid to Jaunty. Every so often (quite often) during typing while using vnc a keys starts get repeated. Pressing the key on the physical keyboard does not help at all. -noxdamage and -norepeat options do not help either :( When I tried -grabkbd, at some point during vnc session I could no longer get any key input, nor get access to some menus... 

Any solution other than restarting X every 5min? :(

kszys.

---

### Post by cybergalvez on 2009-05-04
I just installed x11vnc to get around the jaunty-compiz-vino problem, and now this problem pops up.  in my case it wasn't a's but spaces, I had to kill the x server (acutally killed the user entirely) to make the problem stop.

---

### Post by ScottCh on 2009-05-04
I'm getting this problem consistently too, and it's a severe pain because my computer system is in a different room connected via KVM extender.  So I have to use x11vnc to see its display.  I'm seriously considering reverting back to Intrepid Ibex, as painful as that would be.  Like others who've posted, I have been using Intrepid, most recently, and all the way back to Breezy without seeing this problem.  I upgraded to Jaunty yesterday and it started happening soon afterward.

I find that if I kill x11vnc and then hit a key on the physical keyboard, the key repeating stops.  I've considered using the -loop option in x11vnc so that I could just kill the process and have it restart, but that also means I have to restart the VNC viewer and set it up.  Do this a every five to ten minutes for a while and you'll start feeling like this :frown: this :mad: and this :evil:

But to keep it all in context, Ubuntu is wonderful, volunteers are the best people in the world, and gracious thanks to the folks who handle these requests.

Scott C. in Cary, NC USA

---

### Post by krunge on 2009-05-04
> **ScottCh said:**
> 
I find that if I kill x11vnc and then hit a key on the physical keyboard, the key repeating stops.  I've considered using the -loop option in x11vnc so that I could just kill the process and have it restart, but that also means I have to restart the VNC viewer and set it up.

If you or anyone else wants to help debug this issue consider compiling and running the following code:

```

/*
 * xkeytest.c: use XTEST extension to inject a few keystrokes. 
 * compile:    cc -o xkeytest xkeytest.c -L /usr/X11R6/lib -lX11 -lXtst
 * run:        ./xkeytest
 */

#include <stdio.h>
#include <unistd.h>
#include <X11/Xlib.h>
#include <X11/extensions/XTest.h>
#include <X11/keysym.h>

int main(void) {
        KeySym syms[16];
        Display *dpy = XOpenDisplay(NULL);
        int i, n = 0;

        if (dpy == NULL) {
                fprintf(stderr, "XOpenDisplay failed.\n");
                return 1;
        }

        fprintf(stderr, "In 1 secs we inject 'hi mom' ...\n");
        sleep(1);

        syms[n++] = XK_h;
        syms[n++] = XK_i;
        syms[n++] = XK_space;
        syms[n++] = XK_m;
        syms[n++] = XK_o;
        syms[n++] = XK_m;
        syms[n++] = XK_Return;

        for (i = 0; i < n; i++) {
                KeyCode key = XKeysymToKeycode(dpy, syms[i]);
                XTestFakeKeyEvent(dpy, key, True,  CurrentTime); 
                XTestFakeKeyEvent(dpy, key, False, CurrentTime);
        }
        XCloseDisplay(dpy);
        return 0;
}

```

This uses the same method x11vnc uses to inject keystrokes: XTestFakeKeyEvent().

So if you can reproduce the problem with this simple program it would be useful to the Xorg developers trying to debug this because it narrows down the possibilities a great deal.

It injects the characters 'hi mom' by the same XTEST method that x11vnc uses.

To do it, save the above in a file named "xkeytest.c" then run the cc compile line mentioned at the top of the code (you will need gcc, libx11-dev, and libxtst-dev packages installed.)

You could run it in an endless loop like this:

```

#  while [ 1 ]; do ./xkeytest; done

```

I suggest opening a 2nd terminal and typing "cat" in it and leaving the mouse focus in that terminal.  Then the hi mom's are printed into that terminal.

You can't use the desktop when this test is going on.  Maybe leave it running overnight or during dinner, etc.

Post back here what you find.  If you reproduce the bug, then add it to the bug report as a 'To reproduce'.

---

### Post by NoThanksM$ on 2009-05-05
Tried this last night and looks like it did NOT reproduce the problem.  Was stil successfully outputting "hi mom" this morning when I checked.

---

### Post by clmorse on 2009-05-05
I think I have run into this also!  Are there any workarounds?  I really need to get vnc working again as I have two remotely managed recently upgraded jaunty boxes.:confused:

---

### Post by ScottCh on 2009-05-05
Hi Krunge,

I wasn't able to build it because my Jaunty system doesn't have libXtst.a.  It has the shared library libXtst.so.6.1.0, but not the static version.  I have build-essential installed on this machine, but it doesn't seem to provide all of the X development libraries.

I tried building it with "gcc -o keytest -I/usr/include keytest.c -shared -L /usr/lib -lX11 -lXext /usr/lib/libXst.so.6.1.0 instead.  This built the program successfully but it immediately segfaults.  

Whatever the case, from what others have reported it does not appear to cause the key repeat problem to occur.

Thanks,

Scott C. in Cary, NC USA

---

### Post by krunge on 2009-05-05
> **ScottCh said:**
> I wasn't able to build it because my Jaunty system doesn't have libXtst.a.  It has the shared library libXtst.so.6.1.0, but not the static version.  I have build-essential installed on this machine, but it doesn't seem to provide all of the X development libraries.


In my post I mentioned libxtst-dev, did you install it?  It might be named something slightly different, but my guess it is that.

---

### Post by TabascoGremlin on 2009-05-05
I have also been having this problem. 

I was able to fix the issue by starting x11vnc with the -clear_keys option. 

(e.g. x11vnc -clear_keys)

I am using ssh to my remote server and then connecting to localhost:x via 
vncviewer localhost:x (where x is the display number set up in .x11vncrc)

I did have to restart the x11vnc service a couple of times, but it seems to work rather reliably on the second call using the -clear_keys

[http://www.karlrunge.com/x11vnc/faq.html#faq-stop-bg](http://www.karlrunge.com/x11vnc/faq.html#faq-stop-bg) is the source of my information

---

### Post by krunge on 2009-05-06
How long (e.g. how much typing) does it typically take to reproduce this problem?

---

### Post by ScottCh on 2009-05-06
> **krunge said:**
> In my post I mentioned libxtst-dev, did you install it?  It might be named something slightly different, but my guess it is that.

Hi Krunge,

I overlooked that library, sorry.  After building the application successfully, I let it run for several minutes and the problem (endless key repeats) did not occur.  I'll try a longer test later.

Regarding how long it takes to occur, it is a fairly short interval for me.  On my development system it begins happening after ten or fifteen minutes unless I'm not using the keyboard.  I have usually typed fewer than a few hundred characters by this point.  It never starts right away.

I can try adapting your xkeytest program to generate many more characters on a line and see what affect it has.

I tried the -grabkbd option for x11vnc and found that after a while, my mouse clicks were no longer behaving properly.  I could use them to select windows, but not activate menus or buttons.  This may be related, because it worked properly for the first several minutes.

I'm going to try the -clear_keys option and see if it helps next.

Scott C. in Cary, NC USA

---

### Post by krunge on 2009-05-06
I upgraded a machine in my basement to ubuntu 9.04, and I was able to reproduce the problem!

It appears to be related to x11vnc turning off and on the key repeating.

So everyone try disabling this feature to see if it provides a workaround:
```
x11vnc -repeat ...

```
**DO NOT** add any other x11vnc options mentioned in this thread.  Just take your normal x11vnc command and add "-repeat" to it.

Please report back here what you see--whether positive or negative.

---

### Post by ScottCh on 2009-05-07
> **krunge said:**
> 
So everyone try disabling this feature to see if it provides a workaround:
```
x11vnc -repeat ...

```
**DO NOT** add any other x11vnc options mentioned in this thread.  Just take your normal x11vnc command and add "-repeat" to it.

Please report back here what you see--whether positive or negative.

Hello Krunge,

I don't want to jinx anything by saying this, but I started using the "-repeat" option yesterday afternoon, and so far the stuck down key problem has not happened.  The results are very promising, but I'd like to try it for a bit longer before pronouncing it cured.

Any idea why it didn't start happening until Jaunty?

Thanks very much, sure hope this is the fix.

Scott C. in Cary, NC USA

---

### Post by krunge on 2009-05-07
> **ScottCh said:**
> 
Any idea why it didn't start happening until Jaunty?


Not sure anyone knows yet, but hopefully someone will start working on it:

[http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/367136](http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/367136)

[http://bugs.freedesktop.org/show_bug.cgi?id=21454](http://bugs.freedesktop.org/show_bug.cgi?id=21454)

---

### Post by ScottCh on 2009-05-08
Hello Krunge,

Just to add a bit more spice to the problem, there seems to be a related bug that occurs less often.  I've only had it happen twice so far, and it took much longer to occur.  The mouse button seems to be "stuck down" instead of one of the keyboard keys.

For example, I'll try to move the cursor from one place to another in the editor, and I wind up highlighting all of the text inbetween instead.  Clicking the mouse has no effect, highlighting is turned on permanently.

This also extends to any component that displays a list.  Instead of picking one, it highlights from the beginning of the list to wherever I click.  So instead of opening one message, I get several windows opening on the display.

Using the "-repeat" option on x11vnc has no effect on this problem.  It took over 24 hours of use to appear instead of ten minutes though.

The "mouse button down" problem is difficult to clear without logging out of the X session.  I was able to clear it by killing x11vnc, leaving x.org (ctrl-alt-F1) and then returning (ctrl-alt-F7).  Closing the active window had no effect, nor did closing the current application.

Thanks again for looking into this problem.

Scott C. in Cary, NC USA

---

### Post by NoThanksM$ on 2009-05-08
Scott,  I can't be sure but I think the problem is actually that the Cntrl key is "stuck down," not the mouse button.  I think I've had it happen to me once or twice as well, although I'm pretty sure it hasn't since i started using the -repeat option (maybe I just haven't given it enough time).

---

### Post by krunge on 2009-05-09
> **NoThanksM$ said:**
> Scott,  I can't be sure but I think the problem is actually that the Cntrl key is "stuck down," not the mouse button.  I think I've had it happen to me once or twice as well, although I'm pretty sure it hasn't since i started using the -repeat option (maybe I just haven't given it enough time).

Yes, I think this issue is a different problem.

Just tap and release all of the Control and Alt keys on your keyboard to see if that frees the key.

More info here: [http://www.karlrunge.com/x11vnc/faq.html#faq-mod-stuck-down](http://www.karlrunge.com/x11vnc/faq.html#faq-mod-stuck-down)

---

### Post by bj0 on 2009-05-12
> **kszys said:**
> I have the same behaviour since upgraded from Intrepid to Jaunty. Every so often (quite often) during typing while using vnc a keys starts get repeated. Pressing the key on the physical keyboard does not help at all. -noxdamage and -norepeat options do not help either :( When I tried -grabkbd, at some point during vnc session I could no longer get any key input, nor get access to some menus... 

Any solution other than restarting X every 5min? :(

kszys.

I haven't checked this thread in a while because -grabkbd has been working for me (except not being able to use menus, but that's not a big deal).

I think the problem you're talking about 'losing keyboard input' happens to me sometimes after being idle for a while.  It's easy to fix without restarting x11vnc though, I just click on a separate window, then click on the window I was typing into and I can continue typing.

I haven't tried -clear_keys yet.

---

### Post by krunge on 2009-05-12
> **bj0 said:**
> 
I haven't tried -clear_keys yet.

The correct workaround is:

```
x11vnc -repeat ...
```

see my posts above.

---

### Post by jebblue on 2009-05-14
The -repeat option seems to be working thanks! I use x11vnc a lot.

---

### Post by Developer.ca on 2009-05-15
-repeat may be the correct solution to stop the problem from happening but it definitely is not the solution if you are experiencing the problem and need to get into a remote box.  (I tried it by itself and it definitely did not work when my '~' key was pressed).

-repeat -clear_keys is the solution if you are currently experiencing the problem.

---

### Post by krunge on 2009-05-17
> **Developer.ca said:**
> -repeat -clear_keys is the solution if you are currently experiencing the problem.

In all of my tests **-clear_keys** would not unstick the repeating key.  But it seems to have unstuck the key for some people in this thread.

BTW, as you know but perhaps not everyone reading, the **-clear_keys** only has an effect at x11vnc startup and exit: it tries to release all pressed keys then.  So for the bulk of the lifetime of the x11vnc process **-clear_keys** has no effect.

---

### Post by sherl0k on 2009-05-18
Hey krunge,

I too have had this problem. From my tests, -clear_keys got rid of a stuck key that I had in a session (which prompted me to find a solution, bringing me here).

Also adding the -repeat switch seems to have fixed the session from getting a stuck key again, but YMMV.

Thanks for writing such a great VNC server. I've tried others but yours is seemingly the fastest and most stable of the bunch. :D

---

### Post by krunge on 2009-05-18
BTW, for people who like to 'roll their own', I have uploaded a x11vnc-0.9.8.tar.gz source tarball to my site: [http://www.karlrunge.com/x11vnc/#downloading](http://www.karlrunge.com/x11vnc/#downloading)

In it there are some fixes to guard against this problem.  What it does is when it is about to disable the key autorepeating it checks if there are any keys pressed down.  If none are pressed down it goes for it, otherwise it tries again later.

So with the 0.9.8 x11vnc you do not need use '-repeat' and/or '-clear_keys'. If any of you try it please report your experiences in this thread.

---

### Post by jebblue on 2009-05-20
I'd like to thank krunge to, I use this thing every day, makes my laptop screen bigger on my desktop monitor and easier to read. Plus, if I need to pick up the laptop and go to a meeting, everything is right there, unlike a typical VNC session which does not go to the main screen.

---

### Post by kewlito on 2009-06-23
-repeat fixed it for me, thanks

---

### Post by ryan00davis on 2009-06-26
well, i have a fun one, mine likes to repeat the delete and/or backspace keys (so files actually get deleted) as well as sometimes repeating letters.  

im trying -repeat now, but the problem is so sporadic (maybe a couple times/month, but when it comes, it tends to come in groups) that i may not notice a fix for a while.

---

### Post by {CGL}ToWeR on 2009-07-06
> **ryan00davis said:**
> well, i have a fun one, mine likes to repeat the delete and/or backspace keys (so files actually get deleted) as well as sometimes repeating letters.  

im trying -repeat now, but the problem is so sporadic (maybe a couple times/month, but when it comes, it tends to come in groups) that i may not notice a fix for a while.

Ryan Id guess that will be solved with -repeat option as I had similar symptons.

Krunge just like to say thx for awesome software and -repeat fixed a stuck key and now works good for me, on Jaunty 9.04 and its default x11vnc package 0.9.3

x11vnc 0.9.3 is a bit old though released '07 - any reason why a newer version is not in Ubuntu yet?  -clear_keys isnt even recognised.

Cheers anyway!

---

### Post by hokage13 on 2009-08-29
I just ran into this problem where the char 's' goes crazy...

I am using 9.04 64-bit
My current command is *sudo x11vnc -safer -localhost -once -nopw -noxdamage -auth /var/lib/gdm/:0.Xauth -display :0*.  
I will try adding *-repeat* now and hopefully it will work.

---

### Post by krunge on 2009-08-29
> **{CGL}ToWeR said:**
> x11vnc 0.9.3 is a bit old though released '07 - any reason why a newer version is not in Ubuntu yet?  -clear_keys isnt even recognised.
Thankfully x11vnc is no longer orphaned in Debian.  Fathi Boudra picked it up recently and it is now at 0.9.8 in sid and squeeze:

[INDENT][http://packages.debian.org/sid/x11vnc]("http://packages.debian.org/sid/x11vnc")[/INDENT]

---

### Post by hokage13 on 2009-08-30
after using *-repeat*, it seems that I don't experience the keyboard being stuck forever...now when I type, the keys seems to be stuck for a little while.

So, for example, if I want to type "sudo", my input would become "sssssssssudddddddooooo"

Anyone seen this happen?

---

### Post by krunge on 2009-08-31
> **hokage13 said:**
> after using *-repeat*, it seems that I don't experience the keyboard being stuck forever...now when I type, the keys seems to be stuck for a little while.

So, for example, if I want to type "sudo", my input would become "sssssssssudddddddooooo"

Anyone seen this happen?Well, this is the reason why x11vnc's default is '-norepeat':
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-repeated-keys](http://www.karlrunge.com/x11vnc/faq.html#faq-repeated-keys)[/INDENT]
It is unfortunate that to work around the stuck key Xorg/etc bug we must disable this feature by using "-repeat".

See the above faq for more info.  You may be able to use the xset(1) (or DT gui) to configure the keyrepeat delay and make it bigger.  E.g. "xset r rate 660".

---

### Post by psycho2base on 2009-09-17
**-repeat -clear_keys** and problem goes out on my ubuntu 9.04 for now... thanks for advices people =D>

---

### Post by nazarener on 2009-09-25
even after upgrading to 9.04  and using -clear_keys and -repeat i still get the same bug :(

---

### Post by jebblue on 2009-09-26
> **nazarener said:**
> even after upgrading to 9.04  and using -clear_keys and -repeat i still get the same bug :(

Don't know if this will help but here is my x11vnc line:

x11vnc -display :00 -localhost -rfbport 5901 -noxdamage -noclipboard -nosetclipboard -forever -repeat -clear_keys &

I use an SSH tunnel. gSTM GUI makes this easy.

---

### Post by Jurjen de Vries on 2009-12-24
I've used the -repeat function. Problem is gone, but when I hold keys now it is only used once. That's frustrating when I hold the backspace.
Any idea if or when the bug will be fixed? Im using ubuntu 9.10 with X.Org X Server 1.6.4 X Protocol Version 11, Revision 0.

@krunge, thanks a lot for this great software and support.

---

### Post by krunge on 2009-12-24
> **Jurjen de Vries said:**
> I've used the -repeat function. Problem is gone, but when I hold keys now it is only used once. That's frustrating when I hold the backspace.

Are you running the vncviewer on Windows by any chance?  Please look at this thread and see if it is your problem:
[INDENT][http://ubuntuforums.org/showthread.php?t=1344610](http://ubuntuforums.org/showthread.php?t=1344610)[/INDENT]

However when you start x11vnc with "-repeat" it should work (since the X server should do repeating.)  Double check that your X server (the one where x11vnc is run) has auto repeat on or otherwise force it on (2nd line below):
```

xset q
xset r on

```

---

### Post by oxmosys on 2010-02-18
That problem is fixed in Lucid alpha 2, therefore migrating to this LTS when it will be stable will probably make everyone happy :-)

---

### Post by gigahz on 2011-03-23
> **ScottCh said:**
> 
I tried the -grabkbd option for x11vnc 

yup that worked for me :D

---

