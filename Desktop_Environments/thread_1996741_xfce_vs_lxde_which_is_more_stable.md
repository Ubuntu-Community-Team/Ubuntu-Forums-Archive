---
title: "xfce vs lxde which is more stable?"
date: 2012-06-04
forum: Desktop Environments
---

### Post by arcull on 2012-06-04
Hi everyone. I've just installed lubuntu 12.04 a few days ago and more ore less I'm happy with lxde. But from time to time once/twice a day pcmanfm and gnome mplayer (maybe some other app as well) crashes. Therefore I was thinking about switching to xfce. So the question is why do this crashes occure? Can it be that using my /home partition from previous installation (Ubuntu 10.10) with all setting from gnome causes the problem? If not, is xfce according to your experiences less buggy? Thanks for suggestions, bye

---

### Post by kellemes on 2012-06-04
lxde is basically openbox + some standard apps is it? (correct me if I'm wrong) Cannot imagine that's unstable or buggy.
Try starting the crashing apps from a terminal window and wait for the crash to occur.. maybe the output in your terminal window gives some usefull info..
For me Xfce is stable as well..
Also it may help to delete/rename the settings-folders from crashing apps, so new and clean setting-files will be created. With every new version of apps setting-files may change, simply moving /home/* to the next version of Ubuntu will cause problems eventually.

---

### Post by anaconda on 2012-06-04
I have never tested lxde, but have been using xubuntu 12.04 on 2 machines for a while now.

I am very happy with it. Has not crashed once yet. Have lost sound a few times, but reboot helped with that, 

The only mildly annoying bug is that sometimes ( = 1-2 times a day) mouse graps a window, that is being clicked. And wont release it before I click (or double-click) again. 
Similar than moving a window by pressing Alt and right-cliking on a window, except that the window wont be released when you stop pressing the mousebutton...  

Hope that will be fixed soon

Some others are experiencing the same problem.
[http://ubuntuforums.org/showthread.php?t=1908474](http://ubuntuforums.org/showthread.php?t=1908474)

Just want to say. I am very happy with xubuntu and I recommend you to try it too.

---

### Post by arcull on 2012-06-04
thanks, hmmm maybe I have problems because of old /home folder, how could I erase all unnecessary stuff (old settings...) could I delete all hidden folders, I mean the ones starting with a  dot. Or is it better to create a new user and copy my current data there. Thanks again.

---

### Post by anaconda on 2012-06-04
dont delete all those dot folders.
some programs wont like it...

Better to make a new user

---

### Post by Rex Bouwense on 2012-06-04
There is no correct answer to your original question.  Both are stable and are used by people for various reasons.  Occasionally settings from a previously installed version have caused problems That is not the rule but rather the exception.  I have used both Lubuntu and Xubuntu and have settled on Lubuntu.  It is fast even on an older system with less RAM.  You have to consider what you want to do with your computer.  
As to deleting the .folders, I don't think that is a good idea.  Which applications are crashing and under what conditions?  If there are just one or two, it is better to deal with them individually rather than trying to remove a wart with a machette.

Two finger slow typing gets beat out again.

---

### Post by drawkcab on 2012-06-04
XFCE 4.10 is a bit buggy for me but 4.8 (xubuntu) has been really solid.

I like lxde but if you have the resources to run xfce I don't see why you wouldn't.

---

### Post by arcull on 2012-06-05
> There is no correct answer to your original question.  Both are stable  and are used by people for various reasons.  Occasionally settings from a  previously installed version have caused problems That is not the rule  but rather the exception.  I have used both Lubuntu and Xubuntu and have  settled on Lubuntu.  It is fast even on an older system with less RAM.   You have to consider what you want to do with your computer.  
As to deleting the .folders, I don't think that is a good idea.  Which  applications are crashing and under what conditions?  If there are just  one or two, it is better to deal with them individually rather than  trying to remove a wart with a machette. Thanks, I understand what you mean, but my first impression was that lxde is buggy. That was a wrong or at least unjustified assumption, however all I want now is a much as possible stable desktop. I'll try to create a new user and see if this solves my issue, thanks again.

---

### Post by Peripheral Visionary on 2012-06-05
LXDE is a newer project than Xfce. In fact it "borrows" a lot of code from Xfce, but it's Openbox (Window Manager) base is very stable. It's the stuff they've put on top of Openbox that is less stable, but lots of folks use it trouble-free.

On my computer LXDE (on minimal Ubuntu) was buggy and crashy, while on a friend's PC it was solid and trouble-free.  I use Xfce (Xubuntu 12.04) now because nothing ever crashes, it's lightweight and fast, and offers considerably more configurability than LXDE does. It's trouble-free on my aging hardware. As long as it doesn't tax my hardware heavily enough to slow it down, I'll keep using Xfce.  

So the real question is, "which is more stable *on my hardware?*" And the only way to find out is to try them both out.

I discovered and adopted LXDE's file manager. I find that PCManFM simplifies things for me even more than Thunar (the Xfce file manager), and I like the Leafpad editor. So I mix 'n' match a little bit of LXDE with my Xfce. :)

---

### Post by snowpine on 2012-06-05
If you run an application from the Terminal, it will provide more output. If/when an app crashes, you can use the Terminal error messages to troubleshoot why it crashed.

Ubuntu bugs are tracked on Launchpad: [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
So you can search if other users have experienced the same crash, and if not, file a bug report. :)

---

### Post by Frogs Hair on 2012-06-05
Having tried both like many others it's  really a question of resources. LXDE is lighter and they both ran well for me .

---

### Post by 3Miro on 2012-06-05
Stability is something that depends on the hardware as well as user patterns. I can only attest for my experience, LXDE is lighter, XFCE is more stable.

OpenBox is about as stable as it can be, however, LXpanel and PCManFM have been buggy. I had an old laptop and I used LXDE for the light-weight, however, PCManFM was so buggy that I ended up using Thunar anyway (LXDE with Thunar). Also, XFCE has been around longer and it plays rather well with non-xfce programs (it used to have integration for the old Gnome 2 panel applets for example).

I am sure other people have had better experience than me, but if LXDE is giving you some hard time, XFCE is definitely worth a try.

Note that if a program in itself is buggy, it will be buggy in any desktop environment.

---

### Post by IWantFroyo on 2012-06-05
In my experience, XFCE is extremely stable.

---

### Post by SylvesterYoo on 2013-04-05
It all boils down to what you want to do with your computer. If you don't really care about fancy looks and themes and all that, then go for LXDE. It's more stable, and Xfce had crashed on me for 5 times (Linux Mint Xfce and Fedora 17 Xfce spin). But then if you got the resources, why not go for Xfce?

---

### Post by VanillaMozilla on 2013-04-05
If two programs are crashing, then fix or replace them.  The desktop is probably not at fault, and you don't have to replace the whole desktop.  For file management, for example, you can easily use Nautilus or Thunar.

An even more conservative approach is just to recreate the configuration files for those programs that are crashing.  The easy, conservative way to do that is just to rename the folder.  For example, rename ~/.mplayer ~/.mplayer.saved .  (.mplayer is a hidden folder in your home directory, i.e. your login directory.)  Mplayer will probably just automatically create a new default folder and you're (hopefully) done.

---

