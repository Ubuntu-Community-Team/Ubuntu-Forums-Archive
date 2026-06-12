---
title: "Greeter app crashing on gdm load"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Ahriman on 2006-06-06
Since upgrading to Dapper, I have had a little bit of trouble when I go to log into Ubuntu. Basically, when the screen flickers as it loads up X, it *should* bring up my logon screen, but instead, flickers another few times (as if it's changing from text-mode to graphical-mode) then brings up a dialog box saying "The greeter application appears to be crashing. Click OK to try another one". This then brings up a basic logon screen, which then works perfectly.

Everything else in Dapper is working without troubles at all. I have tried editing my xorg.conf to load up fglrx for my gfx card (Radeon 9550), then I tried ati, and none of it makes any difference. Any ideas on this one?

PS: I tried the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=138321"), but keep getting a 404 when I try to download the file. I don't seem to be having the exact same problem, as I can get into my X session, it doesn't dump me to the console at all.

---

### Post by Ahriman on 2006-06-07
*bump*

---

### Post by Ahriman on 2006-06-08
*bump*-ing again

Anyone?

---

### Post by scxtt on 2006-06-08
this used to happen to me, kinda infrequently, using breezy, hasn't yet w/ dapper ... i'm not sure why it happens, but it was so infrequent that it wasn't an issue ... there were also a few times when X would load, but it get a lot of "snow" on the screen - like it was caught between a normal login and what happens when the cable goes out ... hitting Ctrl+Alt+Backspace would fix the problem - but i never got to the bottom of either problem ...

it might not be happening now cause i'm using the fglrx drivers for my ATI X850Pro, i think in the past i'd used vesa, then radeon (if ever), and ati ...

---

### Post by justinjstark on 2006-06-17
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/48936](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/48936)

---

### Post by ogami1972 on 2006-09-28
did you ever get this fixed? it's my last task, and i can't seem to get it fixed....

---

### Post by justinjstark on 2006-09-28
Nope, it still happens here and the launchpad bug is still open.  Maybe it will be fixed in edgy????

---

### Post by gosh on 2006-10-04
> **blaksaga said:**
> Nope, it still happens here and the launchpad bug is still open.  Maybe it will be fixed in edgy????

I'm running edgy and it is still happening to me...

---

### Post by arpitjain11 on 2007-07-20
I am having the same problem. I am using Debian machine. Initially it popups twice saying the same error of "greeter application could not be started. attempting to start a new one" .. and then a blank screen. .. no idea what is the problem .. it was working fine till yesterday .. 

till yesterday it was giving the error that "greeter application could not be started" .. but after clicking "OK" in that, normal login screen used to come which is not coming now.

---

### Post by raydar on 2007-10-13
Yikes!  I went and upgraded my UbuntuStudio Feisty to Gutsy on release candidate day, and everything was working fine, including dual monitors with my nvidia card.

Then around noon today, one kernel-related and one other update became available, so I applied both.  I finished copying several GB of files from my old Ubuntu drive (which I'd upgraded to Gutsy before release candidate day and had fatal grub/kernel and nvidia driver trouble with) and rebooted, and since then I've been getting the problem this thread is about.

I can switch to a different tty, delete xorg.conf (I saved a renamed copy, of course), and boot to a single monitor, but I have to do that, rather than just edit "nvidia" to read "nv" in the couple of driver entries in xorg.conf where it appears.

Anybody else get this?  

(Reverting to a previous kernel in grub doesn't help, but I'm not sure whether that's directly related; I haven't messed with this installation's settings much at all, though.)

---

### Post by YTTK on 2007-10-13
raydr,

I am back to single screen. Latest updates broke dual screen just like yours. greeter application crash as soon as 2nd screen is an anabled and reboot. I hope someone has a solution otherwise I will have to go back to windows XP.

---

### Post by kry0_bpr on 2007-10-13
i installed gutsy 2 days ago.. everything working 100% .. dual monitor.. compiz fusion.. nvidia 6600gt card.. then today.. applied some updates.. now.. cant boot.. on gdm load.. it continuously says.. greeter application crashed on load.. trying another.. then nvidia on screen logo.. then some console stuff about /etc/rc.local.. then same greeter crash message again.. arGH!!.. anyone help?

---

### Post by thoRHCT on 2007-10-13
I went through an update today - and on the next reboot I get the same error message.

---

### Post by kry0_bpr on 2007-10-13
managed to fix it!.. 

edit /etc/gdm/gdm.conf

alter the Greeter= variable.. 

so.. you now have in the conf :

    65 # The greeter for attached (non-xdmcp) logins.  Change gdmlogin to gdmgreeter
     66 # to get the new graphical greeter. 
     67 Greeter=/usr/lib/gdm/gdmlogin
     68 


so instead of gdmgreeter.. im using gdmlogin.. it comes up 'debian login' when i go to boot x/gdm.. but i can login and all is well again :).. back to compiz/fusion 3d excellence! .. dunno what/why this latest update has caused this.. but that fixed it.. for me.. 

let me know if that helps!!!

kry0/bpr

---

### Post by raydar on 2007-10-13
I tried editing gdm.conf as you suggested, also putting my xorg.conf file back.  Unfortunately, I got the same problem as before, notwithstanding Greeter=/usr/lib/gdm/gdmlogin in gdm.conf (and nvidia as the driver in xorg.conf). :\

But thanks for the lead--maybe it'll fix other folks'.  Maybe I should try your fix but without any xorg.conf, but I think not having the nvidia driver specified would make dual monitors impossible.

Is there anything else in gdm.conf that could be tried?  I haven't looked at that file before.

---

### Post by kry0_bpr on 2007-10-13
bah.. sorry to hear that it didnt fix it for you.. hmm.. ok.. ill include my gdm.conf.. followed by xorg.conf.. then u can see if im doin much diffo than you.. 

thanks.. kry0  (attached z ips)

---

### Post by thoRHCT on 2007-10-13
I modified edit /etc/gdm/gdm.conf as you suggested. It works for me! 
Thanks.

---

### Post by plutino on 2007-10-13
You'll probably have to modify the file

/etc/alternatives/gdm-config-derivative

as well.  It works for me after I modified this file to use gdmlogin.


> **raydar said:**
> I tried editing gdm.conf as you suggested, also putting my xorg.conf file back.  Unfortunately, I got the same problem as before, notwithstanding Greeter=/usr/lib/gdm/gdmlogin in gdm.conf (and nvidia as the driver in xorg.conf). :\

But thanks for the lead--maybe it'll fix other folks'.  Maybe I should try your fix but without any xorg.conf, but I think not having the nvidia driver specified would make dual monitors impossible.

Is there anything else in gdm.conf that could be tried?  I haven't looked at that file before.

---

### Post by YTTK on 2007-10-13
Thanks, kry0_bpr work around worked like a champ.

---

### Post by JymmyZ on 2007-10-13
> **plutino said:**
> You'll probably have to modify the file

/etc/alternatives/gdm-config-derivative

as well.  It works for me after I modified this file to use gdmlogin.

Thank you!  I had the same problem with not being able to use GDM after the latest round of updates.  Changing just gdm.conf did not work, but once I changed this second file I could get a login screen (ugly as sin, but I can login now at least)

---

### Post by raydar on 2007-10-14
Plutino, you had the second piece of my puzzle--kry0_bpr, you had the first.  After I changed the Greeter= setting in both 

/etc/gdm/gdm.conf 

and 

/etc/alternatives/gdm-config-derivative 

from gdmgreeter to gdmlogin, all is well again; both screens with nvidia driver. 

Do y'all just know this stuff?--'cause I wouldn't ever have come up with those two things. :)  The login prompt I got had a big Gnome footprint on it, as opposed to identifying itself as Debian, as described above.  Also, it'll be interesting to see what the next update does--will it fix the problem kry0_bpr and Plutino have fixed, and when it does, will it put the Greeter= settings back to gdmgreeter, or will we have to re-edit gdm.conf and gdm-config-derivative back manually?

In any case, THANKS FOR A GOOD FIX! :)

---

### Post by eviltandem on 2007-10-14
Changing the line in gdm.conf worked for me as well.

---

### Post by Twintop on 2007-10-14
Worked for me as well. Thanks!

---

### Post by raydar on 2007-10-15
Just thought I'd report on what happened for me after the rest of this weekend's batches of updates, including this morning's (15 Oct.):

The first of them re-broke the login (as per the subject of this thread) by changing Greeter= back to "gdmgreeter" in the file /etc/alternatives/gdm-config-derivative only; it didn't touch /etc/gdm/gdm.conf.  I just changed the former back to "gdmlogin" and all was well.

A subsequent update popped up a box asking permission to overwrite gdm.conf, and I said yes, figuring it would likewise re-break the login and I'd just have to edit gdm.conf again.  But it didn't break anything; I still got the Gnome (as opposed to Ubuntu) login we've been relying on as a workaround for the initial problem this thread's about, but hey, everything still works.

Anyone else's experience differ in an interesting way?

---

### Post by YTTK on 2007-10-15
raydar,

After updates today everything is working great! Back to original login with no errors.

:)

---

### Post by lazyrussian on 2007-10-15
I'm having the same problem.

I just changed the /etc/gdm/gdm.conf files and it worked (god it's ugly) lol.

Thanks  for the help!

I'll try changing it back periodically (after updates) to see if it fixes the problem.

---

### Post by lazyrussian on 2007-10-15
I just ran today's updates and it undid my gdm.conf change. So I just changed it back to gdmlogin again and it's still working. Hopefully I/we wont have to endure this ugly splash for  long.

---

### Post by raydar on 2007-10-15
Me too.  I had found one file still reading gdmlogin after one round of updates, but another update gave me the Ubuntu[Studio] login instead of the Gnome one.

Since then I a new realtime kernel came down the pipe for UbuntuStudio, and that left me without X successfully starting--but that's for another thread.

Thanks again for the help.  

(Is this getting to be a solved thread?)

---

### Post by lazyrussian on 2007-10-15
I think this will be a solved thread once everyone can get back to using gdmgreeter over gdmlogin.

As I mentioned earlier, I;m still stuck with gdmlogin (and I only had to edit one file). I think there should be/hope there will be another one or two gdm updates before the final release, or there is going to be a sh*tstorm on the forums about this.

---

### Post by Twintop on 2007-10-16
Just an FYI, the updates that got pushed down last night fixed my problem on the 64-bit version.

---

### Post by lazyrussian on 2007-10-16
I reported the bug to launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/153426](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/153426)

---

### Post by lazyrussian on 2007-10-17
The 32-bit and 64-bit versions have been fixed but the packages are frozen/haven't been pushed down yet. 
It should come through in the next 48 hours.

---

### Post by raydar on 2007-10-17
Awesome--thanks for the Launchpad reporting and the good news!

---

### Post by lazyrussian on 2007-10-18
I've changed the status back to incomplete on the bug report - I misunderstood the guy I was conversing with.

Meh, I'll even take a stab trying to figure out what's wrong.

---

### Post by Crosbie on 2007-10-22
Any progress on this?

---

### Post by lazyrussian on 2007-10-22
Nope, none yet... :(

---

### Post by Crosbie on 2007-10-23
Just tried a logout-login after the latest update.  No change.  

Is there any way of tracing what might be the problem?  Does gdm keep logs?  I'm sure there must be an error log somewhere but I'm too newbish to know where to look...

---

### Post by Crosbie on 2007-10-23
A restart also fails to make any difference.  Grrr!

Seems like this issue occurs in a number of different situations - the solutions for none of which work for me in this one.  Grrr!

---

### Post by Crosbie on 2007-10-28
Sorry to keep posting, but here's an update:

Just updated to the current gdm and the problem still remains.  there's a version called 'Gutsy proposed'... is it worth trying it out?

---

### Post by lazyrussian on 2007-10-28
hmm, there's no new update for me.

---

### Post by Crosbie on 2007-10-28
To clarify: It seems I'm on version 2.20.1-0ubuntu1 (gutsy-proposed), and in Synaptic -> gdm -> Properties -> Versions, it says there's another version available: 2.20.0-0ubuntu6 (gutsy).  

I guess it's just the last version, which didn't work for me anyway.

My current workaround is to autologin as my most common user (ie, me).  If I have to switch I can always logout - and get the same problem (greeter failing, reverts to debian-symbol fallback login).

---

### Post by Budward on 2007-10-31
I have a similar problem, on my HP pavilion dv2036ea. After installing updates from a clean 7.10 install yesterday, and running nvidia-settings to get my monitor back to its correct resolution, I now have the greeter crashing message. 

The screen goes the correct colour, and the spinning cursor appears, and then it flickers back to the console and tries again. It does this three times before giving me the "Greeter application appears to be crashing" message.

Editing gdm.conf to gdmlogin has not helped - I see the GNOME login start to appear (as opposed to the greeter), and then it flickers back again, and the error message reappears. After this, I end up with a plain orange screen with a cursor on it, and nothing to click! gdm-config-derivative does not appear to exist on my system - when I tried to edit it vim created a new file.

This is very very frustrating - I don't appear to be able to actually DO anything with my shiny new installation. Any help anyone can offer would be greatly appreciated. I'll point out now that I am a complete newb, so am likely to need solutions spoonfeeding to me!

---

### Post by koara on 2007-11-02
Same problem, but after upgrade from a (working) feisty to gutsy about a week ago. 

I looked around the internet and none of the suggested things helped (and i bet some of them hurt). To summarize:

1) since yesterday, normal boot gives me 'greeter crashing', but shell login works ok. I may have installed some updates as recommended by the system before the problems started, but i saw no errors/didn't have to hack at anything.

2) changing Greeter in gdm.conf to gdmlogin allows me to select the user in a GUI, but still a crash follows ("session lasted less than 10s"). xsession-errors says 
"(process:6082): Gtk-WARNING **: This process is currently running setuid or setgid"
By the time i look, no such process exists anymore.

I have no /etc/alternatives/gdm-config-derivative file like some people mentioned in this thread, so i cannot modify that.

I tried
1) changing access rights/owner in /tmp, .gnome2 and removing xserver.xgl (as per instructions in some other thread) - no effect

2) removing 915resolution, dpkg-reconfiguring xserver-xorg to use intel driver. Seems to be working fine, resolution detected etc., but does not solve the crash problem.

3) removing compiz, compiz-fusion packages. No effect as far as i can tell.


I'm on hp nc6320 laptop, i upgraded from feisty and my linux administration knowledge is limited.

Help anyone? Cheers

---

### Post by koara on 2007-11-03
UPDATE: i tried more stuff, gave up and decided to re-install the whole system. I thought that would be the quickest solution but apparently i was too optimistic... the installation drops me to initramfs prompt with no error message whatsoever O_O 

oh the joys of linux, i'm going to search the forums for another thread :)

---

### Post by lazyrussian on 2007-11-03
Koara, I was about to do the same, but thank you for doing it for me :(
If it makes you feel any better, I had the same ferven optimism that a fresh install would fix anything...lol

---

### Post by Crosbie on 2007-11-04
Was footling around today trying stuff out.  tried changing when gdmm starts by adjust its position in /etc/rc2.d from S13 to S21 (a threa dsuggesting ti was being started too early for X to be ready or something).  This didn't make any odds for me.

A promising lead was trying to run the login prog with debugging messages enabled (following the gnome troubleshooter page).  This spit out complaints about the 'accessibility registry' not being available.  Huh?

---

### Post by cappadonna on 2007-11-16
I had the same issue.  This is what fixed it for me.

System/Administration/Login Window.  When the "Login Window Preferences" window comes up click the "Local" tab.  Change the Theme to Selected Only and Style to Themed.

---

### Post by lazyrussian on 2007-11-16
> **cappadonna said:**
> I had the same issue.  This is what fixed it for me.

System/Administration/Login Window.  When the "Login Window Preferences" window comes up click the "Local" tab.  Change the Theme to Selected Only and Style to Themed.

This does NOT work - at least for me, and now I can't even login to ubuntu! :(

I changed gdm.conf back to gdmgreeter after changing my login preferences and then I restarted my system - I kept getting that error over and over again...

Next, to fix this I logged in via the repair console and tried to fix it manually using vi...
First I changed it back to gdmlogin and then i started X and was logged in as a privileged user, which to my surprise, does not have the administrator-->login window preferences menu item.

Now every time I try starting ubuntu, I get a flashing themed login screen.

I'm on my XP partition now....anyone know how to manually change my login window preferences???

---

### Post by cappadonna on 2007-11-16
> **lazyrussian said:**
> This does NOT work - at least for me, and now I can't even login to ubuntu! :(

I changed gdm.conf back to gdmgreeter after changing my login preferences and then I restarted my system - I kept getting that error over and over again...

Next, to fix this I logged in via the repair console and tried to fix it manually using vi...
First I changed it back to gdmlogin and then i started X and was logged in as a privileged user, which to my surprise, does not have the administrator-->login window preferences menu item.

Now every time I try starting ubuntu, I get a flashing themed login screen.

I'm on my XP partition now....anyone know how to manually change my login window preferences???

Sorry this didn't work for you.  One other note.  Human was my selected theme.  What was happening before was I had "Random From Selected" checked for the Theme and I had multiple themes selected.  From what I could tell when I was getting the greeter error was that it was trying each one of the Themes I had selected until it reached the Human Theme.  Then it would let me login.  That's just my observation.  

Maybe if you can get to point where you can select the Human Theme it will work.

Again sorry.

---

### Post by lazyrussian on 2007-11-16
It was set to human :(

---

### Post by lazyrussian on 2007-11-21
Alright, I've finally sorted this problem out for myself.

Afrer following cappadonna's suggestion, I ended up screwing up my computer a tad bit + that login fix plus some of my own fixes somehow disallowed me from mounting my hardrive on one of the kernels - good think my grub has my old feisty kernel still saved. I logged in through that and backed up all my information onto a spare hardrive.

I then proceeded to do a fresh install of gutsy (I overwrote my nonfunctional gutsy partition and my windows xp partition).

For some strange reason, that DID NOT WORK - I saw nothing after the grub menu came up.
I figured something went wrong with the install.

Instead of trying to do this again, I did a fresh install of feisty and then upgraded to gutsy.

After upgrading to gutsy, everything started working (including gdm and my alsa sound) two of the problems that usually involved a lot of manual work.

The only thing I had to do was re-enable restricted graphics drivers and install xserver-xgl to get compiz working again.

I am writing this on my toshiba laptop, and GDM (gdmgreeter) is 100% functional - I even skinned my login screen :) - [http://www.gnome-look.org/content/show.php/Kalahari+Ubuntu?content=69245](http://www.gnome-look.org/content/show.php/Kalahari+Ubuntu?content=69245)

I don't recommend this methd to everyone but I am simply stating that it works.
If you are for some reason on the edge of wiping your hard drive, do the following:

**THE METHOD THAT WORKED FOR ME (~2 hours w/DSL)**
1) Fresh Install of Feisty
2) Update Feisty (just general updates - do not install any programs yet)
3) Dist-Upgrade to Gutsy
4) Update Gutsy
5) Install all appropriate Graphics Drivers
6) Restart Computer
7) Now you can go nuts and install anything that you want and hopefully your GDM login screen works. :)

---

### Post by mnarinsky on 2007-11-26
Check how much free space do you have left on your hard drive ("df" command could be helpful).

I had 100% used and I had this message.
Cleaning up the hard drive solved the problem..

---

### Post by colonelmac on 2008-03-24
I used this approach and it solved my greeter issues:

 ```
vim /etc/gdm/gdm.conf-custom

```

Clear everything beneath the following field:

```
[greeter]
```

Thus, your file should look something like this:

```

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]

```

This resets your gdm to the non-custom Ubuntu default. The best part was that I didn't have to resort to an "ugly" login screen!

Tell me if it works for ya. :)

---

### Post by Crosbie on 2008-06-29
Thank you - this did the trick for me under Hardy, resetting to defaults and then allowing me to change my preferences as per the System/Login Window GUI.

I think tweaks and kludges over the previous iterations of Ubuntu had let some problems creep in - particularly, I suspect, workarounds for ATI graphics drivers...

---

### Post by Kain000 on 2008-07-06
> **raydar said:**
> I tried editing gdm.conf as you suggested, also putting my xorg.conf file back.  Unfortunately, I got the same problem as before, notwithstanding Greeter=/usr/lib/gdm/gdmlogin in gdm.conf (and nvidia as the driver in xorg.conf). :\

But thanks for the lead--maybe it'll fix other folks'.  Maybe I should try your fix but without any xorg.conf, but I think not having the nvidia driver specified would make dual monitors impossible.

Is there anything else in gdm.conf that could be tried?  I haven't looked at that file before.

Hey are you doing this via the command line or inside the GDM?

---

### Post by raydar on 2008-07-08
It's been long enough I'm afraid I can't really remember. Going back and looking at my own posts & the original, I tend to think I was doing that at the command line, 'cause I think it sounds like my trick was hitting CTRL+ALT+F5 (or whatever F#) and messing with files using nano. 

Habitwise, when given the chance, I use a terminal inside the gui, most often just to sudo gedit instead of use nano.

But my guess-answer (sorry) to your question is at the command prompt.

---

