---
title: "disable tapping alps touchpad in breezy"
date: 2005-10-15
forum: Desktop Environments
---

### Post by djjuice on 2005-10-15
Any ideas how to accomplish this?
The patch for alps touchpads has already been applied in breezy since its using the 2.4.12 kernel. But the alps.readme states that disabling tapping is not really possible without applying this little patch thats not included in the original patch since its been known to cause errors. I read an older thread that pretty much re-compiled the 2.4.10 kernel but i don't need to appply patches since the .12 kernel has thes asforementioned. Has anyone have in solid steps or any way to disable tapping on an alps keypad?

---

### Post by gila_monster on 2005-10-15
[QUOTE=djjuice]Any ideas how to accomplish this?
The patch for alps touchpads has already been applied in breezy since its using the 2.4.12 kernel. But the alps.readme states that disabling tapping is not really possible without applying this little patch thats not included in the original patch since its been known to cause errors. I read an older thread that pretty much re-compiled the 2.4.10 kernel but i don't need to appply patches since the .12 kernel has thes asforementioned. Has anyone have in solid steps or any way to disable tapping on an alps keypad?[/QUOTE]

I don't have an alps touchpad, but I was able to disable tapping on my laptop by editing /etc/X11/xorg.conf thusly:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MaxTapTime"            "0"
EndSection

The important line is the one with MaxTapTime. If it's not there, add it. If it's there, make sure it's set to zero.

With luck, this will help you out.

Gila

---

### Post by djjuice on 2005-10-15
the maxtaptime option only applies to true synaptic touchpads, with an alps touchpad setting maxtaptime 0 and the deafult pointer/mouse setting has no effect.

---

### Post by gila_monster on 2005-10-15
[QUOTE=djjuice]the maxtaptime option only applies to true synaptic touchpads, with an alps touchpad setting maxtaptime 0 and the deafult pointer/mouse setting has no effect.[/QUOTE]

Didn't realize that. Thanks for letting me know.

Gila

---

### Post by William Szostak on 2005-10-19
This has given me lots of trouble, too.
I have a Dell Inspiron 600m with an Alps touchpad.
Installed Ubuntu 5.10, and cannot disable tap-to-click.
Of course I set MaxTapTime to 0 in the xorg.conf file, but it doesn't work with Alps.

I've read everything on the web, most of which refers to older versions of the kernel and they all say you need to rebuild the kernel with the alps.patch.  I read somewhere that the alps.patch was already included in the 2.6.12 kernel, but since I couldn't turn off the tap-to-click I thought maybe that was wrong.  I installed the source and tried to apply the patch, but all patches were already applied.

I read the README.alps, and found the comment that disabling tapping will not work unless you also apply that patch that is shown in the readme.  I copied this patch to a separate file and tried to apply it, but it failed.  I suspect the code in the alps.c has changed since the readme was written so the patch no longer makes sense.  Can anyone confirm this?

The xorg log shows that it is detecting the touchpad, and even shows the value of MaxTapTime as 0.  But tap-to-click is still in effect.

I noticed that the xorg-driver-synaptics version is listed as "0.14.3+revertedto+0.13.6".  Do I need version 0.14.3 to make this work?  Does anyone know why it was reverted?  I can't seem to force the package manager to install the 0.14.3 version.  Do I need to go to the telia website to get this version?  Does anyone know if something will break if I do this?  (I'm just nervouse because it was "reverted".)

The touchpad basically works - it's just that the tap-to-click is way too sensitive and it ends up clicking on things when I'm just trying to move the cursor around the screen.  Very infuriating!  I never know what it's going to think I clicked on!

BTW, my USB mouse works fine, but I need the touchpad when working mobilely.

---

### Post by makhand on 2005-10-20
Bump!

Has anyone gotten their alps touchpad to be able to scroll vertically? I applied the patch in hoary. Do I have to do that again? I'm trying to configure a Dell Inspiron 8500. Is there a howto for this? Scrolling is pretty important to me. thanks!

---

### Post by makhand on 2005-10-22
Anyone with the know how to enable vertical scrolling with alps? this is for my girlfriend's laptop and she's getting pretty impatient.

---

### Post by William Szostak on 2005-10-22
I was finally able to get this working!  I managed to turn off tapping, and the scrolling works, too.

To get this working, I had to install the 0.14.3 version of the Synaptics driver.  Steps are outlined below.

Before you bother with the synaptics upgrade, you might want to try the following quick fix:

```
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"
```

Then reboot.
If this doesn't work, you can try proto=any and reboot again.
The above didn't do anything for me, but it worked for other people according to some of the forums I've read.  If it works for you, great!  If not, then do 

```
sudo rm -f /etc/modprobe.d/psmouse.modprobe
```

and proceed with the following to upgrade your synaptics driver to 0.14.3.

[LIST=1]
[*]In Synaptic Package Manager, install build-essential and libxext-dev.
[*][Download the synaptics-0.14.3.tar.bz2]("http://web.telia.com/~u89404340/touchpad/files/").
[*]Untar it:
```
tar jxvf synaptics-0.14.3.tar.bz2
```
[*]Download this patch: [ATTACH]3098[/ATTACH] and save it into the synaptics-0.14.3 directory that you just untarred.
[*]Cd to that directory and apply the patch:
```
patch -p1 < ubuntu-synaptics-0.14.3.patch.txt
```
(that's a number one following the -p)

[*](Note: with kernel 2.6.12, you do NOT need to apply the patches that are mentioned in the README.alps file)
[*]Build the synaptics library:
```
make
```
[*]make a backup copy of the synaptics driver /usr/X11R6/lib/modules/input/synaptics_drv.o
[*]Install the driver that you just built:
```
sudo make install
```
[*]Make a backup copy of your /etc/X11/xorg.conf file.
[*]Change the /etc/X11/xorg.conf file to have settings that are appropriate for an Alps touchpad.  The default file will make your cursor move really slowly.  This attachment lists the settings from the relevent sections of my xorg.conf file (note: this is not the whole file, just the sections you'll want to change): [ATTACH]3099[/ATTACH]
[*]Reboot.
[/LIST]

I hope this works as well for others as it did for me.  I spent a whole week searching the web and trying different solutions before stumbling on the above.

The following forums provided the info I needed:
[http://ubuntuforums.org/showthread.php?t=75094]("http://ubuntuforums.org/showthread.php?t=75094")
[http://ubuntuforums.org/showthread.php?t=75431]("http://ubuntuforums.org/showthread.php?t=75431")
[http://ubuntuforums.org/showthread.php?t=60494]("http://ubuntuforums.org/showthread.php?t=60494")

Now that my touchpad isn't going crazy, I really like Ubuntu!

Good luck with your gf's laptop, makhand!

-William

---

### Post by stoffe on 2005-10-22
Haven't had the time to try this yet (laptop at other location) but if this works, this is something I hope will get into the repositories as soon as humanly possible. That's the single biggest annoyance I have when running Ubuntu on the laptop.

Thanks! =)

---

### Post by makhand on 2005-10-22
[QUOTE=William Szostak]
Good luck with your gf's laptop, makhand!

-William[/QUOTE]

Hey thanks man. I'll give it a go. Everything seems to work fine in this department on my laptop (compaq), and i was really hoping it would just work on hers as well... but no such luck. I'll let you know how it turns out. This really should be included with the releases (if possible).

---

### Post by Kinux on 2005-10-23
I personally suffered a lot with this problem and Alps touchpad.
After passing a lot of time with Ubuntu 5.04, I abandoned and went back to Fedora.

Now After seeing a new version 5.10 I could not resist to check it out again. Well again the same problem !

But, this time I really wanted this Ubuntu to work, finally, after days and days of reading and experimenting, it worked for me !!

Take a look at your /proc/bus/input/devices file. Mine said :

I: Bus=0011 Vendor=0002 Product=0008 Version=2222
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 ts1 event2
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

So in xorg.conf I changed the lines of the Synaptics section from :

Option         "Device" "/dev/psaux"
Option         "Protocol" "auto-dev"

to :

Option          "Device" "/dev/input/event2"
Option          "Protocol" "event"

Then I added the rest as :

        Option          "LeftEdge" "120"
        Option          "RightEdge" "900"
        Option          "TopEdge" "120"
        Option          "BottomEdge" "5000"
        Option          "MaxTapTime" "0"
        Option          "VertScrollDelta" "20"
        Option          "HorizScrollDelta" "20"
        Option          "MinSpeed" "0.3"
        Option          "MaxSpeed" "0.75"

And It worked just Greate, with vertical scrolling !!
The ButtomEdge is set to 5000 because I didn't like the horizontal scrolling.

For Information, my test Laptop is an old Dell CPXJ.

Hope this helps some of you.

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-27
What about this? Something's not right...

In file included from syndaemon.c:20:
/usr/include/X11/Xlib.h:3575: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3580: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3593: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3606: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3611: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3843: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3847: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3859: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3887: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3891: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3931: error: syntax error before ‘_X_SENTINEL’
make: *** [syndaemon.o] Error 1


...f I turn off my computer now, having followed the first part of the directions, will I not have a working touchpad at ALL again??? How do I get this to work? I haven't sed around with those files, so I don't know why it just magically worked for others but not for me, if they're still as they came...what do I do??

---

### Post by jwolf on 2005-10-27
[QUOTE=William Szostak] -snip- [/QUOTE]


William Szostak, you are a beautiful person. 

My laptop is usable again!


Thanks so much :D

---

### Post by William Szostak on 2005-10-29
SuperDiscoMachine,

Did you apply the patch listed in my steps 4 and 5?
I got those same errors during the make, before I applied the patch.
In answer to your question, if you reboot at this point, nothing should change.  Your touchpad should still work (or not work) as well as it does currently.

Jwolf, 
Thanks for the post.  I was really excited to finally get the touchpad working, and I'm glad it worked for someone else, too.

-WS

---

### Post by emperor on 2005-10-29
Thanks William! Great Howto! My i9300 touchpad is working much better now, no more "hopping" out of window when I type and hit the spacebar, and the scrowl bars in the pad work very well.

I did have a problem appling the patch the "patch" command.
===================================
1. the patch file ends with ".txt"

2. Patch fails with an error.
a. One problem is that the header file it patches is marked read-only!
b. But still fails due do to the following error:
patch: **** strip count l is not a number
c. So I found I had to copy change from the patch file to the header manually.

3. Then I did make and make install.

---

### Post by emperor on 2005-10-29
[quote=Kinux]I 

personally suffered a lot with this problem and Alps touchpad.

Take a look at your /proc/bus/input/devices file. Mine said :

I: Bus=0011 Vendor=0002 Product=0008 Version=2222
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 ts1 event2
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

So in xorg.conf I changed the lines of the Synaptics section from :

Option         "Device" "/dev/psaux"
Option         "Protocol" "auto-dev"

to :

Option          "Device" "/dev/input/event2"
Option          "Protocol" "event"
[/quote]

I would not recommend this solution, as the event# will change for the pad if you boot the computer with an external mouse attached. Both the event and mouse# are not fixed.

---

### Post by William Szostak on 2005-11-05
[QUOTE=emperor]
I did have a problem appling the patch the "patch" command.
===================================
1. the patch file ends with ".txt"
[/QUOTE]
Ok, I updated my posting to include the .txt in the patch command.
(I was forced to add the .txt when uploading the file to the forum and forgot to change the command accordingly.  Thanks for the catch.)

[QUOTE=emperor]
2. Patch fails with an error.
a. One problem is that the header file it patches is marked read-only!
[/QUOTE]
Shouldn't matter because the directory is writable.  The patch command actually moves the original file to a backup (appending ".orig" to the file name) then creates a new copy of the file with the patch applied.  But if you manually changed the file as you state below, then yes, you would have to chmod the file to make it writable.

[QUOTE=emperor]
b.  But still fails due do to the following error:
patch: **** strip count l is not a number
[/QUOTE]
The strip count is the number that follows the -p in the patch command.
Be sure you type a number one, not a lower-case L.
I added a note to my post to try to clarify this as well.

[QUOTE=emperor]
Thanks William! Great Howto! My i9300 touchpad is working much better now, no more "hopping" out of window when I type and hit the spacebar, and the scrowl bars in the pad work very well.
[/QUOTE]
Thanks for the feedback.  I'm glad you got it to work!

---

### Post by SteveGodfrey on 2005-11-10
Do any of you have the mini joystick style mouse? I have a Tecra S1 which has the touchpad and also a small blue mouse joystick above the 'b' key. I want to disable this but I can't find any clue as how to do it. Any ideas?

Thanks

---

### Post by makhand on 2005-11-10
[QUOTE=William Szostak]

Good luck with your gf's laptop, makhand!

-William[/QUOTE]

Again, thanks William. it worked just as you said it would. I am no longer in the doghouse for 'making my girfriend use linux'. 

Steve, why would you want to disable it? When you find your solution, make sure its posted for everyone else to see. I wonder if it might be detected as just another mouse input (something like /dev/input/mice). Check your xorg.conf. I'll have to see if i can find clues on my gf's laptop when i see her again. She has one of those as well. i dont.

---

### Post by robtotheb on 2006-01-16
Thanks!
My new Dell 6000's touch pad work perfectly now.

---

### Post by fheinsen on 2006-02-15
[quote=William Szostak]I was finally able to get this working! I managed to turn off tapping, and the scrolling works, too...[/quote] 
William, thank you.  This worked well for my wife's Inspiron 600m.

---

### Post by qiemem on 2006-02-16
Thank you so much! I can finally use this thing as a laptop... oh, ya, working beautifully with my inspiron 9300. oh one thing to add, looks like synaptics-0.14.4 has been released, though I didn't try it and don't have the time to see if it already has the patch/works with the patch etc... just thought it might be worth noting. Anyway, thanks again! (Yay for awsome scroll action too!!!)

---

### Post by opoplawski on 2006-03-02
Just installed 0.14.4.  The extra ubuntu patch still applies (with a fuzz of 2).

I've decided to leave tapping on but to use syndaemon (with -d -t -k options) to disable tapping while typing as I still like tapping most of the time.  We'll see how that works out.

Thanks William and everyone for posting their info.

---

### Post by vincebs on 2006-03-08
To the previous poster, what did you modify in the patch or in the instructions to get the fix to work with version 14.4?

---

### Post by regebro on 2006-05-26
Thank you William!

All the other instructions failed. This worked. Yay! Now I can work again, after 1.5h of fiddling. (I forgot my mouse at home today and I can't stand the tapping mode on the mousepad). What a relief!

---

### Post by vincebs on 2006-06-11
Anyone get this to work on Dapper Drake, using synaptics-0.14.5?

---

### Post by shaviro on 2006-07-06
I followed William's instructions, using synaptics-0.14.3 on dapper, and it didn't work; after I rebooted, the irritating touch-to-click is still in operation.

I haven't tried synaptics-0.14.4 or 5, because (as per unanswered questions above) I don't know how to do the patch.

---

