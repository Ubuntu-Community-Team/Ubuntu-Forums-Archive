---
title: "Locking icons position"
date: 2012-02-03
forum: Desktop Environments
---

### Post by underkz on 2012-02-03
Hi guys,

I'm wondering if we can kind of "lock icons" on the desktop so they will not change positions when I play a 800*600 game.

You know, when you have icons near the left side of your screen and after playing a game your icons are all smashed to the right side of the screen.

Any clues? Thank's :)

---

### Post by PD808 on 2012-02-03
Oh my god. :o I had this too when I used XFCE. I couldn't find the answer though. I sort of "solved" it by moving all the desktop icons into a second folder called "Desktop", which is on the actual desktop. I placed it in the top left corner of the screen. That's not the best solution though if you want desktop icons on the actual desktop... Hm. Did you try filing a bug report?

---

### Post by Frogs Hair on 2012-02-04
Hello and Welcome 

I don't see anything in the configuration editor or advanced settings that allows what you want . I am curious what allows the icons to move when the game is used . Neither the  configuration editor nor Ubuntu Tweak include a right or left placement option for desktop icons in 11.10 . I am on Ubuntu .so that may not be case for you .

---

### Post by underkz on 2012-02-06
Hi,

thank's for your answers it's appreciated. For more precision I'll add that I run on Xubuntu 11.10

@PD808
your solution is pretty original ;-). I didn't tried to filled a bug report because I didn't think this problem can be considered like a bug. Thank's for this suggestion, maybe it's the way to go.

@Frogs Hair
Well, the thing is when the game resize the screen in a lower resolution all icons change position to be visible for that newer resolution. And after when the desktop regain the normal resolution (when closing a game) it seems that nothing is replacing the icons at their initial position :(.

---

### Post by LewisTM on 2012-02-06
Here's another solution for you. 
Run 
```
sudo chattr +i ~/.config/xfce4/desktop/icons*
```
This in effect renders your icon placement config file immutable.
When you change resolution your icons will be shuffled around and will be out of place when your get back. 
However, the changes will not have been written to disk.
To reload the desktop and the right placement, simply run 'xfdesktop --reload'. This can be conveniently made into a launcher.

To unlock the config, replace +i for -i in the first command.

Cheers!

---

### Post by underkz on 2012-02-06
@LewisTM
Big thank's, that's a useful trick to know. I just need to remember to unlock the file when adding icons to the desktop ;).

---

### Post by jamibair1 on 2012-02-08
Hi Lewis TM
I tried your command, but i got this:

chattr: Ingen sådan fil eller filkatalog while trying to stat /home/mik/.config/xfce4/desktop/icons*

(Sorry, that was danish = "chattr: No such file or folder..."

What went wrong ?

---

### Post by LewisTM on 2012-02-08
> **jamibair1 said:**
> Hi Lewis TM
I tried your command, but i got this:

chattr: Ingen sådan fil eller filkatalog while trying to stat /home/mik/.config/xfce4/desktop/icons*

(Sorry, that was danish = "chattr: No such file or folder..."

What went wrong ?
Well it may be that the dir names are different in Danish?
The full filename is typically 'icons.screen0.rc'
You can try to find it with a search tool or with the locate command.

---

### Post by LewisTM on 2012-02-09
A small trick I just discovered.
The desktop has a built-in reload/refresh function, which is the F5 key, not surprisingly. 
So no real need for the reload command.
If you add or rename items on a locked desktop they will still appear upon reload, except that without any known placement they will be thrown to the next available upper left spot. 
The ~/Desktop dir itself is not locked.

---

### Post by jamibair1 on 2012-02-09
[QUOTE=LewisTM;11672939]Well it may be that the dir names are different in Danish?
The full filename is typically 'icons.screen0.rc'
You can try to find it with a search tool or with the locate command.[/QUOTEm]

Thank you for the answer. I'll now work with this. Am new in Ubuntu, so... Yep! I got work to do.

---

### Post by underkz on 2012-02-09
great tips! thank's!
I hope this will be corrected in the next XFCE version.

---

### Post by jamibair1 on 2012-02-12
I decided to give GNOME the last try, before i surrender and install xubuntu to get the xcfe: So far I got to this in gconfig editor: /desktop/gnome/file_views/icon_theme.
Can I use the "chattr" command here, or am i risking a major explosion then ?

[I]BTW: There's an ongoing discussion dating from 2005-2009 here, but it's way over my head:
[https://bugzilla.gnome.org/show_bug.cgi?id=301615#c1](https://bugzilla.gnome.org/show_bug.cgi?id=301615#c1)[/I]

---

### Post by LewisTM on 2012-02-12
> **jamibair1 said:**
> I decided to give GNOME the last try, before i surrender and install xubuntu to get the xcfe: So far I got to this in gconfig editor: /desktop/gnome/file_views/icon_theme.
Can I use the "chattr" command here, or am i risking a major explosion then ?

[I]BTW: There's an ongoing discussion dating from 2005-2009 here, but it's way over my head:
[https://bugzilla.gnome.org/show_bug.cgi?id=301615#c1](https://bugzilla.gnome.org/show_bug.cgi?id=301615#c1)[/I]
Not at all, the chattr command is for files, not configuration entries. If you can find a file that tells Nautilus (i.e the GNOME desktop manager) where to place icons, that might work. So far I couldn't find one.

---

### Post by jamibair on 2012-02-17
Gee. Am realy fooling around here. Just discovered, that i couldn't login with my jamibair1. Reason is, i've already some time ago created an account: jamibair (probably after a long night with the boys). So sorry!
Enough of that.
As Lewis TM so kindly pointed out, I was using GNOME. Now I've installed Xfce, and tried the command "sudo chattr +1 ~/ etc...". It didn't work, even when i copy paste the entire file name. Then I tried same command without space between +1 and /.config (sudo chattr +1/.config/...), but this time the outcome was this: 
 graanet@graanet-laptop:~$ sudo chattr +i/home/graanet/.config/xfce4/desktop/icons0.rc:
    [LEFT]Usage: chattr [-RVf] [-+=AacDdeijsSu] [-v version] files...
[SIZE=2]What's my mistakes this time ?[/SIZE]

[SIZE=1][/SIZE]
[SIZE=1][/SIZE][/LEFT]

---

### Post by LewisTM on 2012-02-17
> **jamibair said:**
> Gee. Am realy fooling around here. Just discovered, that i couldn't login with my jamibair1. Reason is, i've already some time ago created an account: jamibair (probably after a long night with the boys). So sorry!
Enough of that.
As Lewis TM so kindly pointed out, I was using GNOME. Now I've installed Xfce, and tried the command "sudo chattr +1 ~/ etc...". It didn't work, even when i copy paste the entire file name. Then I tried same command without space between +1 and /.config (sudo chattr +1/.config/...), but this time the outcome was this: 
 graanet@graanet-laptop:~$ sudo chattr +i/home/graanet/.config/xfce4/desktop/icons0.rc:
    [LEFT]Usage: chattr [-RVf] [-+=AacDdeijsSu] [-v version] files...
[SIZE=2]What's my mistakes this time ?[/SIZE]

[SIZE=1][/SIZE]
[SIZE=1][/SIZE][/LEFT]
What do you mean by "it didn't work"? Did you get an error message?
In a terminal, type 
```
sudo chattr +i /home/graanet/.config/xfce4/desktop/icons* 
or 
sudo chattr +i ~/.config/xfce4/desktop/icons* 
```
The +i or -i have to be separate from the filename.

---

### Post by jamibair on 2012-02-17
Ah, Lewis TM, great to hear from you again!

"Usage: chattr [-RVf] [-+=AacDdeijsSu] [-v version] files..."

that was also the reply when i wrote the command, exactly as you posted it should be. But it didn't work.(?)

---

### Post by LewisTM on 2012-02-17
It should work, the error is one of syntax, not of a failure to execute the operation. 
To simplify things, [FONT="Courier New"]cd[/FONT] to ~/.config/xfce4/desktop
then type [FONT="Courier New"]ls[/FONT] to list the files and find the one containing the icons placements, probably called icons.screen0.rc
Then just copy and paste the command:
```
sudo chattr +i icons.screen0.rc
```
If successful, no output should be seen.

BTW welcome to the wonderful world of Xfce! :D

---

### Post by jamibair on 2012-02-17
@LewisTM: Thank you for always fast replies and welcoming :D
I performed the task as instructed, however the icons still happily fly around when I hold down left button and drag.
Am probably still fooling around.

---

### Post by LewisTM on 2012-02-17
> **jamibair said:**
> @LewisTM: Thank you for always fast replies and welcoming :D
I performed the task as instructed, however the icons still happily fly around when I hold down left button and drag.
Am probably still fooling around.
I think you missed a key point. Locking the file prevents the changes from being written to DISK. You can still move icons around but the desktop will forever be amnesic. Press F5 to reload the desktop and see for yourself.
Also this prevents icon PLACEMENT from changing, not anything else (image, name, etc.).

---

### Post by jamibair on 2012-02-18
And that's certainly an improvement regarding my project.
Than you for helping me out:p

---

### Post by stratoka on 2012-11-30
Thanks, it helped on Debian to.

---

### Post by Jussl on 2013-04-22
> **underkz said:**
> Hi guys,

I'm wondering if we can kind of "lock icons" on the desktop so they will not change positions when I play a 800*600 game.

You know, when you have icons near the left side of your screen and after playing a game your icons are all smashed to the right side of the screen.

Any clues? Thank's :)


Finally I came up with decent solution for this.

1. Create following script, save it to your home folder as "RunPreservingIconPos" and make it runnable.

```
#!/bin/bash
cd ~/.config/xfce4/desktop/
cp -f ./icons.screen0-1280x1024.rc ./icons.screen0-1280x1024.rc_bak

# This will launch application given as argument (as background process).
$1 &
sleep 1

# This will get PID of the application (if it launches multiple processes this script might not work).
PID=`jobs -p`
echo "Looking for process which has pid of $PID."

# Let's wait until ps doesn't see the process anymore.
while [ ! -z `ps -p $PID -o pid=` ]; do
sleep 1
done

echo "Execution of the process ended."

cd ~/.config/xfce4/desktop/

# These lines forces new configs to be read (apparently by flushing some config cache).
rm ./icons.screen0-1280x1024.rc
xfdesktop --reload

# Wait and restore backed up configs.
sleep 1
cp -f ./icons.screen0-1280x1024.rc_bak ./icons.screen0-1280x1024.rc
xfdesktop --reload
```

**NOTE! Rename all of these "icons.screen0-1280x1024.rc" filenames in the script to correspond to your resolution in use!**


2. Modify all problem application launchers to start with the script, example:

/usr/games/sauerbraten
--->
/home/<yourusername>/RunPreservingIconPos sauerbraten 


3. Done. After one second you exit the application, all your icons will be just where you wanted.


If you find it useful, please share it.

---

### Post by underkz on 2013-04-22
Thank's for sharing your solution, that's a nice script! But I guess all lines with "icons.screen0-1280x1024" needs to change depending of the resolution adopted.

I really hope that XFCE or xubuntu will do something about it one day .

---

### Post by Jussl on 2013-04-23
Oh yes, you are right. Correct file names are dependent of resolution.

Do you know whether there is bug report filed for this?

---

### Post by underkz on 2013-04-24
**If** I remember right, I think there was a report filed for this, but sadly I do not find it. It seems not to bother many people, so I doubt it will be quickly resolved :?.

---

### Post by Jussl on 2013-06-14
Everyone who are bothered by this issue, please go and mark yourself affected by this bug. Then maybe someone will really fixed it.
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1190990](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1190990)

---

### Post by Jussl on 2014-03-07
Anyone still experiencing this problem with recent Xubuntu? Or should we close the report?
[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1190990](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1190990)

---

