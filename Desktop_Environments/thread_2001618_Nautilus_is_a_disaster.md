---
title: "Nautilus is a disaster"
date: 2012-06-11
forum: Desktop Environments
---

### Post by pmorton on 2012-06-11
Why is Nautilus so unreliable? There's always something with it. For years it has refused to refresh directory contents - what's that about? Then it crashes when dragging files from one window to anther, And now with 12.04 it runs so slowly you think it's crashed. 

Isn't it time this thing was forked by someone who will look after it? It's only about the most important single Ubuntu desktop tool!!!

Frustrated

---

### Post by timcowchip on 2012-06-11
Caja, the Mate DE fork of Nautilus seems to work pretty well.

---

### Post by raja.genupula on 2012-06-11
may i know your system specifications ?

---

### Post by ajgreeny on 2012-06-11
> **raja.genupula said:**
> may i know your system specifications ?
+1
I must ask the same question.

I have been using Ubuntu since version 5.10 (and now part-time using 12.04) on the same machine and I do not recognise the nautilus behaviour you speak of.

---

### Post by Enigmapond on 2012-06-11
I too have been using it for quite some time and have never noticed these issues. It's always run very well and quite stable.

---

### Post by vasa1 on 2012-06-11
A tweak gone wrong?

---

### Post by Morbius1 on 2012-06-11
There are other options you know like Thunar or PCManFM. Both of those are network aware but only PCManFM can bookmark a remote share.

If your focus is on internal files there's XFE - multi-pannel  but not network aware. And it's the only one I mentioned that's a WYSIWYG file manager.

[I]BTW: WYSIWYG in this context can be demonstrated by the following:

Open up nautilus to /usr/share/applications and you see a lot of things with child like names. Now do an "ls -al /usr/share/applications" and you will see the adult names for these files. It comes in handy in Xubuntu where some of these *.desktop files need to be modified to show up on the menu.


[/I]

---

### Post by flemur13013 on 2012-06-11
> *Open up nautilus to /usr/share/applications and you see a lot of things with child like names. ...*I'd never noticed that before.  

Listing bogus filenames is really...bogus - and thunar and pcmanfm act the same way as nautilus.

Thanks for mentioning XFE, it lists the correct file names and also lists files' extensions rather than the pretty useless "mime type".

---

### Post by NadirPoint on 2012-06-11
I don't know if I'd go so far as to call it a "disaster," but I remain perpetually annoyed at it's tendency to randomly crash or disappear upon un-mounting a volume.  I've noticed this behavior through numerous releases and several different hardware combos I run, so any system spec seems irrelevant.

I'll say "unstable."

---

### Post by Frogs Hair on 2012-06-11
Like the others I have not seen this in six releases. Are you using any Nautilus scripts or other tweaks?

---

### Post by mcduck on 2012-06-11
> **flemur13013 said:**
> I'd never noticed that before.  

Listing bogus filenames is really...bogus - and thunar and pcmanfm act the same way as nautilus.

Thanks for mentioning XFE, it lists the correct file names and also lists files' extensions rather than the pretty useless "mime type".

That's simply because Nautilus implements the XDG desktop file spedicication, and thus actually understands the .desktop files and displays the launcher they describe. (this is how you can have program launchers on your desktop, which is of course managed by Nautilus).

So it's not a case of displaying a file with a "bogus filename", but instead a question of interpreting the file and displaying the interpreted information, as any XDG-compliant file manager is supposed to do for a .desktop file. (Which, I agree, can be annoying if your purpose is to edit the .desktop file instead of using it as a launcher).

---

### Post by VanillaMozilla on 2012-06-11
Pmorton, you need to install the debugging information for Nautilus if you can find it, so a crash report will be generated.  Then someone might have a chance at finding the problem.  And they won't even look at a bug report without a stack trace.

But I think I agree with the others that Nautilus has never crashed for me, so I have no idea what the problem could be.

---

### Post by pmorton on 2012-06-11
> **Frogs Hair said:**
> Like the others I have not seen this in six releases. Are you using any Nautilus scripts or other tweaks?

I've got a recent re-install, using 12.04, and no tweaks whatsoever. 

uname -a ->
3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

It's strange the way different people experience this. I've just read others on the net complaining about it being slow under 12.04, and I've read about the refresh issue recently too, but found no answer to it. Yet people here say they haven't experienced any of my difficulties. 

Another beef I have with it is that nautilus scripts (which I have, but am not running any in the context of any of the problems I describe) are so unreliable - sometimes they run and sometimes they don't. It just looks to me over the years that this is a badly maintained programme, for an essential ingredient of an operating system.

I've used XFE and Thunar, but I don't want to change my entire OS, and Thunar has other limitations, like having not script facility (unless I'm out of date). All I want is a file browser that's reliable!

---

### Post by Morbius1 on 2012-06-12
> **pmorton said:**
> and Thunar has other limitations, like having not script facility (unless I'm out of date). 
A minor point the context of this topic but Thunar does in fact have a scripting facility. Open up Thunar and select Edit > Configure custom actions. In fact it's easier to use than a nautilus-script.

But if you think about it if you use Gnome today more that one file manager is required since Nautilus has passed the tipping point. The list of things it cannot do now outweighs the things that it can.

---

### Post by ceratophyllum on 2012-06-12
I couldn't agree more with the name of this thread. Totally unusably slow on my Acer Aspire One ZG5 netbook.  Xfce4/Thunar is a lot more tolerable with the animations, transparency, etc. all off. I'm not certain the problem is in nautilus, but it's crazy that dumb eye-candy brings what would be a perfectly usable computer to its knees.

---

### Post by TorakTu on 2012-06-12
I had nautilus installed for several of the kernel version with the Ubuntu 12.04 install. Yes it does slow down on my computer. But I was under the impression it had to do with my video card driver issues I am experiencing. But then again, it will turn some of my USB sticks into read only mode as well. Frustrating to try to get around that.

---

### Post by ceratophyllum on 2012-06-12
> But then again, it will turn some of my USB sticks into read only mode as well. Frustrating to try to get around that.

I've been fighting with permissions and ownership since I first discovered Linux in 1997. Yeah, yeah, security blah,blah,blah. On a single user system with a bad internet connection (rural 3G) all I do is trip over this needless multiuser complexity. Is it really necessary? How many people actually run a Linux system with more than one user these days? I would venture to guess less than 5% of all Linux users.


And on top of all the permissions sillines, there's this HAL/DBUS whatever deamon, crazy long hex UUIDs.... Was editing fstab,a little thought, and simple /dev/hdaX device names really so terrible?

There's always DropBox. At least, until someone decides more of what isn't broken needs fixing.

---

### Post by TorakTu on 2012-06-12
I would have to agree with you on this. For single user machines such as ours security is a bit much in a lot of these cases. Locking down my USB is just one of the many problems I have had. But then again, I am thankful for the security because I come from a windows background that has none. So I am at odds with myself here.

---

### Post by VanillaMozilla on 2012-06-12
PMorton, please do take my suggestion about submitting a crash report.  That's how to get things fixed.

You might try running Nautilus under Gnome Classic (no effects).  You will have to install gnome-session-fallback if you don't have it already.  In 12.04 I have used Nautilus only a little on an old test machine, but I didn't notice any problem on Gnome Classic (12.04).  Haven't tried it much under Unity.

---

### Post by VanillaMozilla on 2012-06-12
> **ceratophyllum said:**
> I've been fighting with permissions and ownership since I first discovered Linux in 1997. Yeah, yeah, security blah,blah,blah. On a single user system with a bad internet connection (rural 3G) all I do is trip over this needless multiuser complexity.
Huh?  It's easy, really.  Usually you just have Write access to your own user directory, and that's all you need, usually.

But if you want to give other users access, just right click on a file or directory or file and you will get a menu to set user access.  (You have to do this from an account that has Read/Write access to the file, or maybe ownership is required--I forget.)  The menu really is simple to use--just some check boxes.  You don't have to use the complex command-line system.  Don't try to get fancy with groups.

To make changes in the system you need to learn how to use the sudo and gksudo commands (again, you have to do this from an account that has administrative privilege).  From a terminal the command is
sudo <command>
or to start a gui program, it's
gksudo <command>

Example:  gksudo nautilus.
If you still have trouble with this, start a new topic.

---

### Post by ajgreeny on 2012-06-12
> **VanillaMozilla said:**
> Huh?  It's easy, really.  Usually you just have Write access to your own user directory, and that's all you need, usually.

But if you want to give other users access, just right click on a file or directory or file and you will get a menu to set user access.  (You have to do this from an account that has Read/Write access to the file, or maybe ownership is required--I forget.)  The menu really is simple to use--just some check boxes.  You don't have to use the complex command-line system.  Don't try to get fancy with groups.

To make changes in the system you need to learn how to use the sudo and gksudo commands (again, you have to do this from an account that has administrative privilege).  From a terminal the command is
sudo <command>
or to start a gui program, it's
gksudo <command>

Example:  gksudo nautilus.
If you still have trouble with this, start a new topic.
Be very careful, in fact I would advise that you do never change permissions on files that are not in your own user's home unless you really know what you are doing and why you are doing it, or you could make your computer unable to boot.

The OS system files require that certain files and folders have particular permissions; if you change them you could possibly be totally locked out.

---

### Post by VanillaMozilla on 2012-06-12
> **ajgreeny said:**
> Be very careful, in fact I would advise that you do never change permissions on files that are not in your own user's home unless you really know what you are doing...
Don't change anything outside the /home/ directory.

> **ajgreeny said:**
> The OS system files require that certain files and folders have particular permissions; if you change them you could possibly be totally locked out.
Care to elaborate?  Obviously the system needs access to system files, but I'd be astonished if you could change this.

---

### Post by ajgreeny on 2012-06-13
> **VanillaMozilla said:**
> Don't change anything outside the /home/ directory.

Definitely my recommendation, unless you really know exactly what you're doing.  Thre are a few (very few) occasions when I have changed permissions of system files for a particular reason.  For example I need to change permissions of one or two binary executable files in /usr/bin and /usr/sbin in order that I can use output from them, which normally needs root permissions in my conky output.  Neither of the executables is strictly *needed* by the OS, but perhaps you can see the point I am making.
> **VanillaMozilla said:**
> Care to elaborate?  Obviously the system needs access to system files, but I'd be astonished if you could change this.What I mean is that by using **sudo command** or **gksu nautilus** you get temporary root permissions meaning you can change anything about a file; even delete it completely.

There have been a few queries in the forum from people who have set permissions on everything in the root filesystem to 777, giving everyone full read/write/execute permissions on everything.  They thought it would make life simpler for them, or maybe used a bad command accidentally, but with that situation the computer simply will not boot, and there is no easy or simple way to reverse the changes; a re-install of the OS is much quicker.

I hope that clarifies my meaning.

---

### Post by VanillaMozilla on 2012-06-13
Interesting.  I used gksudo to try to change file access for a system directory, and everything was grayed out.  Didn't try the command line, though.  Agreed, though, 777 access for /boot/ is a pretty dumb idea, although I have no idea why that would make it nonbootable. :-s

---

### Post by idiotprogrammer on 2012-06-13
I have been having frequent crashes on 12.04, and 5 minutes ago something directly as a result of Nautilus. 

**[SIZE="3"]I have never had so many crashes on a single OS before[/SIZE]**. happens at least once a day. In this case, I just clicked to a mounted directory contained video files within Nautilius; before it listed all the files,  it froze and then crashed the OS. 

I have started a thread about my crashes. [http://ubuntuforums.org/showthread.php?t=1997103](http://ubuntuforums.org/showthread.php?t=1997103) Some of them seem Unity/Compiz related, but 5 minutes ago  I was inside Nautilus and that was the only application i was actually using. About 1/4 or 1/3 of 12.04 crashes seem to happen when I try to browse through directories in Nautilus. 

One of the problems is that I don't know how to collect crash information. Is there a tool for that? I wish there were a way to do it automatically.I've looked at apport, and it seems that the application uses a nontrivial amount of system resources. But the problem is intermittent, so I don't want to keep it always on.  

Linux kundera-linux 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux Radeon HD 2600XT card.

---

### Post by idiotprogrammer on 2012-06-14
Well, looks like I had another Nautilus crash. Two consecutive ones. 

The time I just described was a directory listing crash. 

For this time, I clicked on a video file twice to launch it with mplayer. Instead it merely froze the nautilus app (and even had a dialog saying that).   The display darkened a bit (a sign in the window manager that something is stuck or frozen). The directories for both crashes were different. 

I tried opening up another TTY, but unsuccessfully because the whole system crashed. During this occasion, I only had two apps. Firefox (with this #$# thread open!), mplayer and nautilus.

---

### Post by pmorton on 2012-06-22
> **Frogs Hair said:**
> Like the others I have not seen this in six releases. Are you using any Nautilus scripts or other tweaks?

No, I am not using any  tweaks.

And the latest oddity I've encountered is that the 'rename' right-click facility if greyed-out, thought it nevertheless works.

---

