---
title: "X not displaying.... can't access desktop interface!"
date: 2005-07-20
forum: Desktop Environments
---

### Post by lostinbeta on 2005-07-20
Hello everyone, I've been having nothing but problems since installing Ubuntu... which is ashame because I know so many people that had no problems and love this thing more than their lives (ok that may be an exaggeration).

I had hostname, root, internet, and resolution issues first.

I managed to fix the hostname/root and internet issues through methods I concocted by searching around this forum.

Then I proceeded to search around to fix my resolution issue because using 640x480 resolution on a 17" LCD monitor just wasn't going to fly with me.

I tryed the various suggestions of fiddling with dpkg-reconfigure xserver-xorg and it never worked... same thing over and over.

I found a solution where someone said if you go into your System BIOS you need to set your integrated video card to use at least 8MB of RAM (I have an integrated card), but I couldn't find anything in my BIOS about setting how much RAM to set for my integrated vid card... so I exited my BIOS and chose the 'exit without saving' option because I didn't want anything saved.... 

So I go to boot up Ubuntu again, I get the log on screen, but I went to log in and I get nothing but a solid brown screen.  Nothing loads.  I can switch from the terminals back to X and restart X using the CTRL+Alt features, but none of this fixes anything.

So I continue to use dpkg-reconfigure xserver-xorg the same as I have to see if maybe I accidently changed a setting... and nope, still won't work.

I did manage to get my resolution working correctly using the 855resolution solution ( [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029) ), and I noticed at the bottom he said someone his X won't dispay, but for him it gets correctly from switching to a terminal then back using CTRL+Alt+F7.  That doesn't work for me.

It worked fine before, so it can't be my vid card.... and it stopped working before the 855resolution solution (I was hoping this might fix the display issue as well).

I have no idea what is going on!  Does anyone have any suggestions?


I tried to search for the answer myself instead of bugging people, but I have no idea what to search for.

---

### Post by Benchrest on 2005-07-20
[QUOTE=lostinbeta]Hello everyone, I've been having nothing but problems since installing Ubuntu... which is ashame because I know so many people that had no problems and love this thing more than their lives (ok that may be an exaggeration).

I had hostname, root, internet, and resolution issues first.

I managed to fix the hostname/root and internet issues through methods I concocted by searching around this forum.

Then I proceeded to search around to fix my resolution issue because using 640x480 resolution on a 17" LCD monitor just wasn't going to fly with me.

I tryed the various suggestions of fiddling with dpkg-reconfigure xserver-xorg and it never worked... same thing over and over.

I found a solution where someone said if you go into your System BIOS you need to set your integrated video card to use at least 8MB of RAM (I have an integrated card), but I couldn't find anything in my BIOS about setting how much RAM to set for my integrated vid card... so I exited my BIOS and chose the 'exit without saving' option because I didn't want anything saved.... 

So I go to boot up Ubuntu again, I get the log on screen, but I went to log in and I get nothing but a solid brown screen.  Nothing loads.  I can switch from the terminals back to X and restart X using the CTRL+Alt features, but none of this fixes anything.

So I continue to use dpkg-reconfigure xserver-xorg the same as I have to see if maybe I accidently changed a setting... and nope, still won't work.

I did manage to get my resolution working correctly using the 855resolution solution ( [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029) ), and I noticed at the bottom he said someone his X won't dispay, but for him it gets correctly from switching to a terminal then back using CTRL+Alt+F7.  That doesn't work for me.

It worked fine before, so it can't be my vid card.... and it stopped working before the 855resolution solution (I was hoping this might fix the display issue as well).

I have no idea what is going on!  Does anyone have any suggestions?


I tried to search for the answer myself instead of bugging people, but I have no idea what to search for.[/QUOTE]


I probably know less about ubuntu than you so consider the source of these ideas before taking my suggestions. But have you tried the ubuntu live cd? Does it work ok? If so I would assume something got screwed up on install and would attempt fresh install taking as many of the default easy install. You shouldn't be having all these problems unless you have very unusual hardware configuration. I am concerned that your solutions to problem 1 are causing number 2 which is causing number 3 etc. Just an idea.

On hostname I used the same name I was using for my computer under windows. It is attached to my XP machine in a lan so I thought using the same name would be good. But really I don't see that it matters what the host name is. You don't need a root user with ubuntu. I created just one user and use sudo for most all root type functions.

Otherwards make the first install as simple as possible, less to go wrong. I am using dual boot on this machine to test migrating applications to ubuntu. Expect it will be sometime before I make the big switch and some applications such as Family Tree maker may never convert as my dad and others use FTM.

Besides an install on my laptop I have tried the live CD on my desktop with no problems other than me.

Rich

---

### Post by lostinbeta on 2005-07-20
I doubt I know more than you, my experience with Linux/Ubuntu goes as far back as yesterday...lol.

The install worked fine, I managed to get Ubuntu installed into another partition (I dual boot with Win XP).  The hostname issue was my fault, but I managed to get that fixed, so the only Ubuntu mistake upon installation was the resolution.  I could log in and get the GNOME desktop interface just fine, just everything was in 640x480.

So I started researching resolution issues (which seems to be a HUGE thing with Linux) and I followed al standard procedures with it.  Still came up 640x480.  Ugh.  So I found that BIOS suggestion, went to check it out, exited without saving because the option wasn't there, and now I can get the login screen just fine, but after that it's just a solid brown background (default Ubuntu background colour) and nothing happens.  No desktop displays.  My computer activity light stops blinking so it's not even trying to load it.

I have access to CTRL+ALT+F1 (and F2, etc), CTRL+ALT+F7 (to get back to the 'desktop' which is solid brown still), and CTRL+ALT+Backspace to restart X.  Restarting X brings me back to the login screen and it just goes around in circles from there.  Those are the only shortcuts I know.  So if anyone has any that open up any APPS in the GNOME desktop I can try those out to see if the apps are accessible or not.

I don't have the slightest idea why this is happening or what files I should look into, or even what I should search this forum for (I have searched to no avail).

---

### Post by lostinbeta on 2005-07-20
Update:

I've tried dpkg-reconfigure xserver-xorg with all the default values (so I could go back to when it was working), this got me back to 640x480 again, but no desktop display still (just a login display).  So I ran the 588resolution thing again and re-edited the xorg.conf file with my HorizSync and VertRefresh values (as specified by requirements for my monitor model) and I got my resolution back, but still no desktop display.

So I thought maybe it was a user thing... because of changes made to the user from the hostname issue.  So I deleted the user and re-created it... still nothing.

So I was recommended by a friend to clear my settings (it was a default install so that wasn't a big deal) using 'rm -rf .g*'  I didn't get any errors, so I'm assuming the clearing of settings worked, but alas, still no desktop.

So, this friend recommended I try running 'ps -aux | grep gnome-session' and I got a syntax error (he doesn't have Ubuntu anymore because his PC fried so he was going off the top of his head).

I tried just running 'ps -aux -w' and it did have some values returned.  I don't know if these are important or not, but anywho...

x-session manager
exit-with-session x-sessi
-fork --print-pid 8 --print-address 6 --session
--exist-with-session x -session manager
keyring-daemon


Those are the processes running under the username logged in.

So my friend tells me to try running gnome-session.  It is supposed to start all the default gnome applications.  Unfortunately I can't do this from within the terminal because I get ...

'Gtk-WARNING cannot open display'

Same happens if I try 'export DISPLAY=:0 gnome-session'


And that is where I am at now.  Still the same spot, but I'm letting you know what I tried thus far to fix it.

---

### Post by lostinbeta on 2005-07-20
I reinstalled Ubuntu, this time getting the hostname crap correct (man i'm dumb)... then I ran 855resolution and BAM I'm back in business.

I'm posting this from Ubuntu again!  YAY!

---

