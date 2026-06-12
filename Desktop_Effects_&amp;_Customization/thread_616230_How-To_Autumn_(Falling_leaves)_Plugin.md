---
title: "How-To: Autumn (Falling leaves) Plugin"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by PatrickFisher on 2007-11-18
Autumn is a Compiz plugin based on Snow. It features movement which is more realistic for leaves.

It can be seen in action [**_here (YouTube)_**]("http://www.youtube.com/watch?v=cHLDtJXc8fg")

To install, download the two attached files to the same directory.

Navigate to that directory in terminal and run:

```
sudo bash ./autumninstall.sh
```

It will ask you if you want to change your desktop background to the one on YouTube. Answer yes/no and you're done!

Go to System>Preferences> Advanced Desktop Effects Settings
enable the plugin and set the toggle key to whatever you want.
Note that if this option is not available, install compizconfig-settings-manager

Enjoy!

---

### Post by venator260 on 2007-11-18
I love it, thanks for putting this up.

---

### Post by AndrewGene on 2007-11-18
Where do I need to put those files??? It is not showing up in Advanced Dekstop Settings.

---

### Post by PatrickFisher on 2007-11-18
> **AndrewGene said:**
> Where do I need to put those files??? It is not showing up in Advanced Dekstop Settings.

Did you run the script?

It should show up.

---

### Post by 469tc on 2007-11-18
> **PatrickFisher said:**
> Autumn is a Compiz plugin based on Snow. It features movement which is more realistic for leaves.

It can be seen in action [**_here (YouTube)_**]("http://www.youtube.com/watch?v=cHLDtJXc8fg")

To install, download the two attached files to the same directory.

Navigate to that directory in terminal and run:

```
bash ./autumninstall.sh
```

It will ask you if you want to change your desktop background to the one on YouTube. Answer yes/no and you're done!

Go to System>Preferences> Advanced Desktop Effects Settings
enable the plugin and set the toggle key to whatever you want.

Enjoy!

Please forgive me for being new to Linux but would you please tell me what the Super key is? As in Super+F11 to activate the Autumn feature. Have everything installed but don't know how to activate...Thanks:)

---

### Post by isaacj87 on 2007-11-18
Hey,

The "Super" key is the Windows logo  key.

---

### Post by Ub1476 on 2007-11-18
Uh, this plugin disabled all my options to enable/disable plugins. How can I fix it?

---

### Post by jarocooke on 2007-11-18
I tried using the script, but it seemed to have trouble with going to the correct folders.  So what I did was just manually input the commands into a terminal.  Works great, nice (and very apt) plugin.

Cheers

---

### Post by mc4man on 2007-11-18
> Uh, this plugin disabled all my options to enable/disable plugins. How can I fix it? 
make sure auto.. plugin sorting is checked (ccsm>preferences>plugins)

---

### Post by patman123 on 2007-11-18
hey great great! plugin i love it and it was easy to install thx again keep it up:)

---

### Post by maduranga on 2007-11-19
wow.. it works.. great. thanks

---

### Post by AJerman on 2007-11-19
I'm at work so unfortunately I'm stuck on my Vista machine and can't try this out, but I'd love to when I get home.

The leaves aren't going to stay behind windows though are they? If they would do that then this would be absolutely brilliant. Otherwise it just ends up like most other effects, something fancy to show off to your friends then never use again. I'm new to Ubuntu though, I don't even know if it's possible to make the effects in the background. From what I understood of it it was just something it was drawing over the screen, so maybe not.

---

### Post by steveneddy on 2007-11-19
This is so cool. My 18 month old grandson lives with me and he kicks the leaves around in the front yard a lot. 

He really got a kick out of this.

Thanks.

:popcorn:

---

### Post by pjones0404 on 2007-11-19
i installed this as well. It is great. i spent about an hour searching for a wallpaper that matched it. It was worth it as this effect is great.

one question that i do have though. As i was running the install in the terminal it prompted me to insert the live cd. i thought that i had all of my repo's turned on but it would not continue until i placed the cd on the tray. why did it do this?

---

### Post by PatrickFisher on 2007-11-19
> **AJerman said:**
> I'm at work so unfortunately I'm stuck on my Vista machine and can't try this out, but I'd love to when I get home.

The leaves aren't going to stay behind windows though are they? If they would do that then this would be absolutely brilliant. Otherwise it just ends up like most other effects, something fancy to show off to your friends then never use again. I'm new to Ubuntu though, I don't even know if it's possible to make the effects in the background. From what I understood of it it was just something it was drawing over the screen, so maybe not.


There is an option for "Leaves over windows".

---

### Post by AJerman on 2007-11-19
> **PatrickFisher said:**
> There is an option for "Leaves over windows".

Oh really, so you can make it just do it behind the windows? I hate to use it to compare, but like DreamScene? If so then I can't wait to get home to download this. If it's practical to keep on at all times, it is a beautiful plugin. :)

---

### Post by jase21 on 2007-11-19
Thanks dude...
Its cool

---

### Post by Espreon on 2007-11-19
Well done! Nice plugin!

---

### Post by PatrickFisher on 2007-11-19
> **AJerman said:**
> Oh really, so you can make it just do it behind the windows? I hate to use it to compare, but like DreamScene? If so then I can't wait to get home to download this. If it's practical to keep on at all times, it is a beautiful plugin. :)

Better than that, it defaults to be behind windows. I don't want a bunch of **** in front of my windows when I'm working.

---

### Post by heelandtoe on 2007-11-19
what directory do i save these files to?

---

### Post by PatrickFisher on 2007-11-19
> **heelandtoe said:**
> what directory do i save these files to?

Any directory. Whatever directory you choose, navigate to it in terminal and run the install script.

---

### Post by jader2toesbumpy on 2007-11-19
really cool dude. thank you

---

### Post by AJerman on 2007-11-19
Okay, yeah, I'm having trouble getting it to show up in my Advanced Desktop Effects Settings app. I ran the script twice and it's still not showing up. Any idea what I'm doing wrong?

**Edit:** [i]Okay, to stop being lazy, I actually read the output and found out that for some reason it wasn't going into it's directories properly. It created ~/.autumn, copied the Autumn.tar.gz file, then tried to do "cd ~/.autumn" and couldn't...

autumninstall.sh: line 5: cd: ~./autumn: No such file or directory

So then it went on to the next command and extracted everything right where I put the files.

I have no idea why it would have a problem opening a folder that it obviously just created, but I'm recently back in Linux after not using it for a while, so I don't know where to further troubleshoot.

Either way, I manually finished the install myself and it works fine now. It looks pretty good, I just need a lot higher resolution wallpaper, anyone got one? I'm running at 1920x1200 so I'll take whatever I can get. :)[/i]

---

### Post by PatrickFisher on 2007-11-19
> **AJerman said:**
> Okay, yeah, I'm having trouble getting it to show up in my Advanced Desktop Effects Settings app. I ran the script twice and it's still not showing up. Any idea what I'm doing wrong?

**Edit:** [i]Okay, to stop being lazy, I actually read the output and found out that for some reason it wasn't going into it's directories properly. It created ~/.autumn, copied the Autumn.tar.gz file, then tried to do "cd ~/.autumn" and couldn't...

autumninstall.sh: line 5: cd: ~./autumn: No such file or directory

So then it went on to the next command and extracted everything right where I put the files.

I have no idea why it would have a problem opening a folder that it obviously just created, but I'm recently back in Linux after not using it for a while, so I don't know where to further troubleshoot.

Either way, I manually finished the install myself and it works fine now. It looks pretty good, I just need a lot higher resolution wallpaper, anyone got one? I'm running at 1920x1200 so I'll take whatever I can get. :)[/i]

Oops. There was a mistake in the install script. My mistake, it should be fixed now.

---

### Post by AJerman on 2007-11-20
> **PatrickFisher said:**
> Oops. There was a mistake in the install script. My mistake, it should be fixed now.

Was there? I thought something seemed wrong, but I didn't have much time to debug it because my roommate was rushing me out the door. Kind of disappointed I didn't notice it immediately though. I guess I need to brush up on my shell scripts a bit now that I'm back in Linux, haha.

Either way, now that it's working I love it. Great job. :)

---

### Post by PatrickFisher on 2007-11-20
> **AJerman said:**
> Was there? I thought something seemed wrong, but I didn't have much time to debug it because my roommate was rushing me out the door. Kind of disappointed I didn't notice it immediately though. I guess I need to brush up on my shell scripts a bit now that I'm back in Linux, haha.

Either way, now that it's working I love it. Great job. :)

Thanks for pointing it out. It never would have shown up as a problem on my system because I made it :P

Damn, it sure is hard to test an install script on a plugin that's already installed.

---

### Post by GotAlotOf?s on 2007-11-21
I am very new to Ubuntu and Linux in general. I would love to use this Plugin but i just don't know how. I read the steps and saved the 2 files on my desktop but don't really understand  what to type in the directory in the terminal. Can anyone write it out for me? Thankz

---

### Post by GotAlotOf?s on 2007-11-21
I went to "How to navigate in terminal" and figured it out. I guess I should have done a little more research. N E waz, thank you for the plugin:)

---

### Post by PatrickFisher on 2007-11-21
> **GotAlotOf?s said:**
> I went to "How to navigate in terminal" and figured it out. I guess I should have done a little more research. N E waz, thank you for the plugin:)

I'm glad you figured it out! Welcome to Ubuntu, make sure that you use these support forums to the max.

---

### Post by baqai on 2007-11-21
i am having few problems here being a noob

All goes well till the following, this code is from my second attempt at installing it

```

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/x/x11proto-xinerama/x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mkdir: cannot create directory `/home/baqai/.autumn': File exists
drwxr-xr-x patrick/patrick   0 2007-11-18 10:54 images/
-rw-r--r-- patrick/patrick 11335 2007-11-17 08:07 images/leaf6.png
-rw-r--r-- patrick/patrick 261139 2007-11-17 08:36 images/DefaultBackground.jpg
-rw-r--r-- patrick/patrick   9497 2007-11-17 08:05 images/leaf3.png
-rw-r--r-- patrick/patrick   9255 2007-11-17 08:04 images/leaf1.png
-rw-r--r-- patrick/patrick  11339 2007-11-17 08:04 images/leaf2.png
-rw-r--r-- patrick/patrick  11173 2007-11-17 08:06 images/leaf5.png
-rw-r--r-- patrick/patrick  10278 2007-11-17 08:06 images/leaf4.png
-rw-r--r-- patrick/patrick 101877 2007-11-18 10:36 images/plugin-autumn.svg
-rw-rw-r-- patrick/patrick     16 2007-11-18 02:01 plugin.info
-rw-rw-r-- patrick/patrick  16338 2007-08-06 19:48 Makefile
-rw-rw-r-- patrick/patrick   4052 2007-11-18 11:25 autumn.xml.in
-rw-r--r-- patrick/patrick  17807 2007-11-18 08:28 autumn.c
./autumninstall.sh: line 7: cd: Autumn: No such file or directory
make: *** No rule to make target `build/autumn.lo', needed by `c-build-objs'.  Stop.
make: *** No rule to make target `build/autumn.lo', needed by `c-build-objs'.  Stop.
Would you like to install the default background (the one shown on YouTube) (yes/no)?  

```

---

### Post by PatrickFisher on 2007-11-21
> **baqai said:**
> i am having few problems here being a noob

All goes well till the following, this code is from my second attempt at installing it

```

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/x/x11proto-xinerama/x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mkdir: cannot create directory `/home/baqai/.autumn': File exists
drwxr-xr-x patrick/patrick   0 2007-11-18 10:54 images/
-rw-r--r-- patrick/patrick 11335 2007-11-17 08:07 images/leaf6.png
-rw-r--r-- patrick/patrick 261139 2007-11-17 08:36 images/DefaultBackground.jpg
-rw-r--r-- patrick/patrick   9497 2007-11-17 08:05 images/leaf3.png
-rw-r--r-- patrick/patrick   9255 2007-11-17 08:04 images/leaf1.png
-rw-r--r-- patrick/patrick  11339 2007-11-17 08:04 images/leaf2.png
-rw-r--r-- patrick/patrick  11173 2007-11-17 08:06 images/leaf5.png
-rw-r--r-- patrick/patrick  10278 2007-11-17 08:06 images/leaf4.png
-rw-r--r-- patrick/patrick 101877 2007-11-18 10:36 images/plugin-autumn.svg
-rw-rw-r-- patrick/patrick     16 2007-11-18 02:01 plugin.info
-rw-rw-r-- patrick/patrick  16338 2007-08-06 19:48 Makefile
-rw-rw-r-- patrick/patrick   4052 2007-11-18 11:25 autumn.xml.in
-rw-r--r-- patrick/patrick  17807 2007-11-18 08:28 autumn.c
./autumninstall.sh: line 7: cd: Autumn: No such file or directory
make: *** No rule to make target `build/autumn.lo', needed by `c-build-objs'.  Stop.
make: *** No rule to make target `build/autumn.lo', needed by `c-build-objs'.  Stop.
Would you like to install the default background (the one shown on YouTube) (yes/no)?  

```

Apt is trying to install the required files from the CD. I'm guessing this is because you upgraded/installed from a CD. Edit your sources.list file to use the online repositories instead of the CD.

---

### Post by baqai on 2007-11-22
Thank you it worked, looks awesome i am surprised that i did had my installation in the dvd in the drive yet it gave me that error

---

### Post by deoki on 2007-11-22
This is awesome!

You sir, deserve 10000 interwebs! :)

Keep up the fantastic job!

---

### Post by Crashmaxx on 2007-11-25
This is really cool, thanks for sharing.

Only one problem, this had something like 100 dependencies, a whole bunch were dev packages. I'm sure most of these aren't really needed, be nice if that could be fixed.

OT: Where can I get the original snow plugin for Gutsy?

---

### Post by Lord C on 2007-11-25
Anyone have a nice theme to go with this?

---

### Post by dmber on 2007-11-25
this is SO awesome!!!!!!

thank you so much.

side note: is there a snow plugin for compiz fusion?  if someone has one that is as easy to install as this one was that would be awesome.

thanks.

---

### Post by BriGaid on 2007-11-25
i second the autumn theme request.

Great job on this plugin.  Do you have any others like it?

---

### Post by nandotron on 2007-11-25
Hi,

I've got the exact same problem, tried changing my sources to deselect the cd in my sources list but still no luck.  is there something i can do to manually create the necessary file or directory?

Thanks!

Enda

---

### Post by Tomosaur on 2007-11-25
Very cool plug-in, nice to have in the background!

---

### Post by PatrickFisher on 2007-11-25
> **nandotron said:**
> Hi,

I've got the exact same problem, tried changing my sources to deselect the cd in my sources list but still no luck.  is there something i can do to manually create the necessary file or directory?

Thanks!

Enda

Try manually running the commands in autumninstall.sh. If the dependencies line gives you troubles, trying installing the packages through synaptic.

---

### Post by PatrickFisher on 2007-11-25
> **BriGaid said:**
> i second the autumn theme request.

Great job on this plugin.  Do you have any others like it?

Not myself, but I'm working on combining Autumn, Snow, Fireflies, and Stars into one plugin to reduce code duplication. It'll take some time though, I'm in the middle of final exams.

---

### Post by Radon on 2007-11-25
Kudos PatrickFisher!  Great plugin!

The best part is the installation script.  Would it be possible to make it universal instead of messing about with git for other plugins?  Perhaps something like OpenSuSE's One-click install for Ubuntu?

---

### Post by PatrickFisher on 2007-11-25
> **dmber said:**
> this is SO awesome!!!!!!

thank you so much.

side note: is there a snow plugin for compiz fusion?  if someone has one that is as easy to install as this one was that would be awesome.

thanks.

compiz-fusion-plugins-unofficial
compiz-fusion-plugins-unsupported

One of those guys includes it. If not, have a go at this:

[http://forum.compiz-fusion.org/showthread.php?t=208](http://forum.compiz-fusion.org/showthread.php?t=208)

---

### Post by PatrickFisher on 2007-11-25
> **Radon said:**
> Kudos PatrickFisher!  Great plugin!

The best part is the installation script.  Would it be possible to make it universal instead of messing about with git for other plugins?  Perhaps something like OpenSuSE's One-click install for Ubuntu?

Hmmm... I'm afraid that I highly doubt this. The install script is merely a shell script that runs the necessary commands automatically so you don't have to. Honestly, I cannot see this method working in a general case.

---

### Post by dmber on 2007-11-25
> **PatrickFisher said:**
> compiz-fusion-plugins-unofficial
compiz-fusion-plugins-unsupported

One of those guys includes it. If not, have a go at this:

[http://forum.compiz-fusion.org/showthread.php?t=208](http://forum.compiz-fusion.org/showthread.php?t=208)
what repo do i need for those?

---

### Post by PatrickFisher on 2007-11-25
> **dmber said:**
> what repo do i need for those?

They would be in the multiverse.

---

### Post by alexlinebrink on 2007-11-25
Install script didn't work, but I still got it (had to delete "CD Autumn" tar in the script)  This is awesome!@

---

### Post by 213374U on 2007-11-26
Can't get this up and running. Read something on the last page about changing repos from CD to online in the sources.list file...... not clear on how to do this. Sorry, still learning.

---

### Post by TadH on 2007-11-26
what command do i use to navigate to the files from the terminal thanks fellas

---

### Post by PatrickFisher on 2007-11-26
> **TadH said:**
> what command do i use to navigate to the files from the terminal thanks fellas

"cd" changes directories. so if you downloaded it to a folder called "Autumn" your home directory, you'd type:

```
cd ~/Autumn
```

Or, to a folder on your desktop:


```
cd ~/Desktop/Autumn
```

---

### Post by McQuaid on 2007-11-26
I've seen some people talking about it working in front of or behind windows.  I'd personally prefer it stay behind any active window.  But what I've always wondered about these plugins is, is it still actively running even though the desktop doesn't have focus, or more accurately a maximized window does have focus.  

It would be nice to be able to leave effects like this on, and know that when you can't see your desktop, it's not animating falling leaves that'll never be seen and  wasting cpu for nothing.

---

### Post by PatrickFisher on 2007-11-26
> **McQuaid said:**
> I've seen some people talking about it working in front of or behind windows.  I'd personally prefer it stay behind any active window.  But what I've always wondered about these plugins is, is it still actively running even though the desktop doesn't have focus, or more accurately a maximized window does have focus.  

It would be nice to be able to leave effects like this on, and know that when you can't see your desktop, it's not animating falling leaves that'll never be seen and  wasting cpu for nothing.

I don't know why anybody would want leaves in front of windows, but I left the option in nonetheless. 

Now, Autumn does still run when there's a window over it. However, you really need not worry about wasted CPU time. I typically have 80-100 leaves running and there is absolutely no slow down. It takes about 1500 leaves for me to notice any kind of slow down at all.

---

### Post by bscoder on 2007-11-26
Doesn't seem work for me. =(

Has build errors due to missing file "autumn_options.h". And that's after I had to create the /usr/share/ccsm and Autumn directories just to get it to the end of the install and ask me if I wanted to install the background.

---

### Post by PatrickFisher on 2007-11-26
> **bscoder said:**
> Doesn't seem work for me. =(

Has build errors due to missing file "autumn_options.h". And that's after I had to create the /usr/share/ccsm and Autumn directories just to get it to the end of the install and ask me if I wanted to install the background.

autumn_options.h is automatically generated. I don't know why it would be missing. Try running the script commands one by one and see what happens.

---

### Post by bscoder on 2007-11-26
Oops, I didn't look closely enough at all of the output - apparently the package "compiz-bcop" can't be found... Is this only for U7.10? I am running 7.04.

Also, I had to create the "Autumn" directory inside .autumn -- the install script appears to be expecting it to be in the archive file, but it isn't. (Or something related to missing compiz-bcop caused it to not be created elsewhere as it should be.)

---

### Post by kodak on 2007-11-26
Crazy :lolflag:

---

### Post by dyerotic on 2007-11-26
ive read this entire post...but i have issues still
i literally just installed ubuntu 7.04....when i type "sudo bash ./autumninstall.sh" it says  bash: ./autumninstall.sh: no such file or directory.....what do i do? i am really excited to see this

---

### Post by kodak on 2007-11-26
> **dyerotic said:**
> ive read this entire post...but i have issues still
i literally just installed ubuntu 7.04....when i type "sudo bash ./autumninstall.sh" it says  bash: ./autumninstall.sh: no such file or directory.....what do i do? i am really excited to see this

are you in the directory where the two files are?

you should cd to where the files are, say there in /home

cd /home

then 

sudo bash ./autumninstall.sh

---

### Post by dyerotic on 2007-11-26
i have to download files? please, i am sorry, i am a n00b...but im tryin

---

### Post by kodak on 2007-11-26
> **dyerotic said:**
> i have to download files? please, i am sorry, i am a n00b...but im tryin

If you look at the first post in this thread you will see two files, put them in your /home directory. open up a terminal and

cd /home

---

### Post by dyerotic on 2007-11-26
holy @$# those files wont DL for soem reason...i click them, the dl thing pops up, i put them in the home dir, but they dont dl...wtf?

---

### Post by dyerotic on 2007-11-26
ok so i dled them
but it wouldnt let me dl them to my home direcotry...only my user one...then when i try to drag and drop says i dont have access....wtf?

---

### Post by PatrickFisher on 2007-11-26
> **dyerotic said:**
> ok so i dled them
but it wouldnt let me dl them to my home direcotry...only my user one...then when i try to drag and drop says i dont have access....wtf?

Where are you trying to drag and drop them to?

---

### Post by dyerotic on 2007-11-26
from my file dyerotic (my username) to home...it doesnt matter tho....when i opened the terminal and did ls, i saw them and it let me do the install...im at 71% illl let you guys know haha

---

### Post by dyerotic on 2007-11-26
it seems to work, then i get this at the very end
./autumninstall.sh: line 7: cd: Autumn: No such file or directory
cp: target `/usr/share/ccsm/images' is not a directory
convert   : autumn.xml.in -> build/autumn.xml
bcop'ing  : build/autumn.xml -> build/autumn_options.h/bin/sh: --header=build/autumn_options.h: not found
make: *** [build/autumn_options.h] Error 127
bcop'ing  : build/autumn.xml -> build/autumn_options.h/bin/sh: --header=build/autumn_options.h: not found
make: *** [build/autumn_options.h] Error 127
Would you like to install the default background (the one shown on YouTube) (yes/no)?  

??

---

### Post by dyerotic on 2007-11-26
i think its because those 2 files arent in my home directory....they are just in my folder dyerotic...i can see them when i just use basic terminal and hit ls...but when i do cd /home...i cant see them, i just see dyerotic....

so cd /hom gets me to root@pablo:/home# then i do ls and i get dyerotic...and dyerotic is where those 2 files are...then wont let me put them in home...says i dont have access

---

### Post by PatrickFisher on 2007-11-26
> **dyerotic said:**
> from my file dyerotic (my username) to home...it doesnt matter tho....when i opened the terminal and did ls, i saw them and it let me do the install...im at 71% illl let you guys know haha

No, you wouldn't have access to /home

Your "home" folder it actually "/home/username" or just "~". It is the folder your terminal should start in.

---

### Post by dyerotic on 2007-11-26
well both those files are in the folder ~...but when i do home it doesnt recognize them

---

### Post by PatrickFisher on 2007-11-26
> **dyerotic said:**
> well both those files are in the folder ~...but when i do home it doesnt recognize them

run:

```
sudo bash ~/autumninstall.sh
```

---

### Post by mistabroadway on 2007-11-26
For some reason it wouldn't install the wallpaper.  I just grabbed it manually so it works great.  Thanks for putting this up.

---

### Post by dyerotic on 2007-11-26
guys i have both files...i need help...wtf is wrong with my ish....

both those files are in my folder....do i need to do anything to those files in the folder? i really wanna get this running

---

### Post by bscoder on 2007-11-27
I think it doesn't work on 7.04 - at least not without some extra work, which I'm too lazy to bother with at present.. And I'm not so sure it would look too great stretched across my 2 monitors anyway - the wallpaper image itself gets a bit blocky with such a stretch.

---

### Post by Niklas Schröder on 2007-11-27
sweet plug-in!

my bro loves it!  :P

brother: *looks at falling leaves* that's awesome!
me: yup.  sure is little bro!  too bad it's LINUX ONLY!
brother: *bangs screen* nooooooooooo!  all the cool stuff is for linux!  *pouts*

i kid you not.  this is a true story.  ;)

i feel sorry for him (and the rest of my family).  they're still stuck in the eye-candy-less world of windoze...

p.s.  i *know* they're eye-candy for windoze, i just don't find it as appealing.  :p

---

### Post by fitzefatze on 2007-11-28
@PatrickFisher

Works just great, thank you for your effort!

---

### Post by 213374U on 2007-11-28
Ran the install. Everything seemed to go fine, asked me if I wanted to install default background, then no Advanced Desktop Effects showed up. Check the code out below and see if you can help me. Feisty user.

Thanks

```
compiling : autumn.c -> build/autumn.loIn file included from autumn.c:43:
build/autumn_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:96: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:109: error: expected declaration specifiers or '...' before 'CompActionCallBackProc'
build/autumn_options.h:110: error: expected declaration specifiers or '...' before 'CompActionCallBackProc'
autumn.c:74: error: expected specifier-qualifier-list before 'CompTexture'
autumn.c:101: error: expected specifier-qualifier-list before 'PaintOutputProc'
autumn.c: In function 'autumnThink':
autumn.c:123: error: dereferencing pointer to incomplete type
autumn.c:125: error: dereferencing pointer to incomplete type
autumn.c:127: error: dereferencing pointer to incomplete type
autumn.c:128: error: dereferencing pointer to incomplete type
autumn.c:133: error: dereferencing pointer to incomplete type
autumn.c: In function 'stepLeafPositions':
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:160: error: 'TRUE' undeclared (first use in this function)
autumn.c:160: error: (Each undeclared identifier is reported only once
autumn.c:160: error: for each function it appears in.)
autumn.c:162: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:163: error: dereferencing pointer to incomplete type
autumn.c:164: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:175: error: dereferencing pointer to incomplete type
autumn.c:175: error: 'CompWindowTypeDesktopMask' undeclared (first use in this function)
autumn.c:176: warning: implicit declaration of function 'addWindowDamage'
autumn.c:176: warning: nested extern declaration of 'addWindowDamage'
autumn.c:180: warning: implicit declaration of function 'damageScreen'
autumn.c:180: warning: nested extern declaration of 'damageScreen'
autumn.c:183: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:187: error: expected declaration specifiers or '...' before 'CompAction'
autumn.c:188: error: expected declaration specifiers or '...' before 'CompActionState'
autumn.c: In function 'autumnToggle':
autumn.c:195: warning: implicit declaration of function 'getIntOptionNamed'
autumn.c:195: warning: nested extern declaration of 'getIntOptionNamed'
autumn.c:196: warning: implicit declaration of function 'findScreenAtDisplay'
autumn.c:196: warning: nested extern declaration of 'findScreenAtDisplay'
autumn.c:196: warning: assignment makes pointer from integer without a cast
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:206: error: 'TRUE' undeclared (first use in this function)
autumn.c:207: warning: control reaches end of non-void function
autumn.c: In function 'setupDisplayList':
autumn.c:231: error: dereferencing pointer to incomplete type
autumn.c:233: error: 'LeafScreen' has no member named 'displayList'
autumn.c:233: warning: implicit declaration of function 'glGenLists'
autumn.c:233: warning: nested extern declaration of 'glGenLists'
autumn.c:235: warning: implicit declaration of function 'glNewList'
autumn.c:235: warning: nested extern declaration of 'glNewList'
autumn.c:235: error: 'LeafScreen' has no member named 'displayList'
autumn.c:235: error: 'GL_COMPILE' undeclared (first use in this function)
autumn.c:236: warning: implicit declaration of function 'glBegin'
autumn.c:236: warning: nested extern declaration of 'glBegin'
autumn.c:236: error: 'GL_QUADS' undeclared (first use in this function)
autumn.c:238: warning: implicit declaration of function 'glColor4f'
autumn.c:238: warning: nested extern declaration of 'glColor4f'
autumn.c:239: warning: implicit declaration of function 'glVertex3f'
autumn.c:239: warning: nested extern declaration of 'glVertex3f'
autumn.c:247: warning: implicit declaration of function 'glEnd'
autumn.c:247: warning: nested extern declaration of 'glEnd'
autumn.c:248: warning: implicit declaration of function 'glEndList'
autumn.c:248: warning: nested extern declaration of 'glEndList'
autumn.c: In function 'beginRendering':
autumn.c:256: error: dereferencing pointer to incomplete type
autumn.c:257: warning: implicit declaration of function 'glEnable'
autumn.c:257: warning: nested extern declaration of 'glEnable'
autumn.c:257: error: 'GL_BLEND' undeclared (first use in this function)
autumn.c:259: warning: implicit declaration of function 'glTexEnvf'
autumn.c:259: warning: nested extern declaration of 'glTexEnvf'
autumn.c:259: error: 'GL_TEXTURE_ENV' undeclared (first use in this function)
autumn.c:259: error: 'GL_TEXTURE_ENV_MODE' undeclared (first use in this function)
autumn.c:259: error: 'GL_MODULATE' undeclared (first use in this function)
autumn.c:261: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:264: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:264: error: 'FALSE' undeclared (first use in this function)
autumn.c:268: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:268: error: dereferencing pointer to incomplete type
autumn.c:272: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:274: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:275: error: dereferencing pointer to incomplete type
autumn.c:276: error: dereferencing pointer to incomplete type
autumn.c:278: warning: implicit declaration of function 'enableTexture'
autumn.c:278: warning: nested extern declaration of 'enableTexture'
autumn.c:278: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:279: error: 'COMP_TEXTURE_FILTER_GOOD' undeclared (first use in this function)
autumn.c:283: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:285: warning: implicit declaration of function 'glTranslatef'
autumn.c:285: warning: nested extern declaration of 'glTranslatef'
autumn.c:288: warning: implicit declaration of function 'glRotatef'
autumn.c:288: warning: nested extern declaration of 'glRotatef'
autumn.c:289: warning: implicit declaration of function 'glCallList'
autumn.c:289: warning: nested extern declaration of 'glCallList'
autumn.c:289: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:300: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:306: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:314: warning: implicit declaration of function 'disableTexture'
autumn.c:314: warning: nested extern declaration of 'disableTexture'
autumn.c:314: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:319: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:320: error: dereferencing pointer to incomplete type
autumn.c:326: error: 'LeafScreen' has no member named 'displayList'
autumn.c:333: error: 'GL_REPLACE' undeclared (first use in this function)
autumn.c:334: error: dereferencing pointer to incomplete type
autumn.c:336: warning: implicit declaration of function 'glDisable'
autumn.c:336: warning: nested extern declaration of 'glDisable'
autumn.c:337: warning: implicit declaration of function 'glBlendFunc'
autumn.c:337: warning: nested extern declaration of 'glBlendFunc'
autumn.c:337: error: 'GL_ONE' undeclared (first use in this function)
autumn.c:337: error: 'GL_ONE_MINUS_SRC_ALPHA' undeclared (first use in this function)
autumn.c: At top level:
autumn.c:345: warning: type defaults to 'int' in declaration of 'ScreenPaintAttrib'
autumn.c:345: error: expected ';', ',' or ')' before '*' token
autumn.c:379: warning: type defaults to 'int' in declaration of 'CompTransform'
autumn.c:379: error: expected ';', ',' or ')' before '*' token
autumn.c: In function 'initiateLeaf':
autumn.c:407: error: dereferencing pointer to incomplete type
autumn.c:409: error: dereferencing pointer to incomplete type
autumn.c:412: error: dereferencing pointer to incomplete type
autumn.c:418: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:426: error: dereferencing pointer to incomplete type
autumn.c:432: error: dereferencing pointer to incomplete type
autumn.c:439: error: dereferencing pointer to incomplete type
autumn.c: In function 'setLeafTexture':
autumn.c:449: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:450: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:450: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c: In function 'updateLeafTextures':
autumn.c:457: error: dereferencing pointer to incomplete type
autumn.c:458: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:462: error: dereferencing pointer to incomplete type
autumn.c:464: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:466: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:468: warning: implicit declaration of function 'finiTexture'
autumn.c:468: warning: nested extern declaration of 'finiTexture'
autumn.c:468: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:469: warning: implicit declaration of function 'glDeleteLists'
autumn.c:469: warning: nested extern declaration of 'glDeleteLists'
autumn.c:469: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:472: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:473: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:474: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:476: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:480: error: 'CompMatrix' undeclared (first use in this function)
autumn.c:480: error: 'mat' undeclared (first use in this function)
autumn.c:483: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:484: warning: implicit declaration of function 'readImageToTexture'
autumn.c:484: warning: nested extern declaration of 'readImageToTexture'
autumn.c:484: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:485: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:485: error: dereferencing pointer to incomplete type
autumn.c:486: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:487: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:488: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:490: warning: implicit declaration of function 'compLogMessage'
autumn.c:490: warning: nested extern declaration of 'compLogMessage'
autumn.c:490: error: dereferencing pointer to incomplete type
autumn.c:490: error: 'CompLogLevelWarn' undeclared (first use in this function)
autumn.c:491: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:491: error: dereferencing pointer to incomplete type
autumn.c:494: error: dereferencing pointer to incomplete type
autumn.c:494: error: 'CompLogLevelInfo' undeclared (first use in this function)
autumn.c:495: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:495: error: dereferencing pointer to incomplete type
autumn.c:497: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:498: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:500: error: 'LeafTexture' has no member named 'dList'
autumn.c:501: error: 'LeafTexture' has no member named 'dList'
autumn.c:501: error: 'GL_COMPILE' undeclared (first use in this function)
autumn.c:503: error: 'GL_QUADS' undeclared (first use in this function)
autumn.c:505: warning: implicit declaration of function 'glTexCoord2f'
autumn.c:505: warning: nested extern declaration of 'glTexCoord2f'
autumn.c:505: warning: implicit declaration of function 'COMP_TEX_COORD_X'
autumn.c:505: warning: nested extern declaration of 'COMP_TEX_COORD_X'
autumn.c:505: warning: implicit declaration of function 'COMP_TEX_COORD_Y'
autumn.c:505: warning: nested extern declaration of 'COMP_TEX_COORD_Y'
autumn.c:506: warning: implicit declaration of function 'glVertex2f'
autumn.c:506: warning: nested extern declaration of 'glVertex2f'
autumn.c:508: error: 'LeafTexture' has no member named 'height'
autumn.c:509: error: 'LeafTexture' has no member named 'height'
autumn.c:509: error: 'LeafTexture' has no member named 'width'
autumn.c:510: error: 'LeafTexture' has no member named 'width'
autumn.c:511: error: 'LeafTexture' has no member named 'height'
autumn.c:512: error: 'LeafTexture' has no member named 'height'
autumn.c:512: error: 'LeafTexture' has no member named 'width'
autumn.c:513: error: 'LeafTexture' has no member named 'width'
autumn.c:523: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:525: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:525: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c: In function 'autumnInitScreen':
autumn.c:536: error: dereferencing pointer to incomplete type
autumn.c:539: error: dereferencing pointer to incomplete type
autumn.c:543: error: dereferencing pointer to incomplete type
autumn.c:546: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:547: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:548: error: 'FALSE' undeclared (first use in this function)
autumn.c:549: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:551: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:563: warning: implicit declaration of function 'WRAP'
autumn.c:563: warning: nested extern declaration of 'WRAP'
autumn.c:563: error: 'paintOutput' undeclared (first use in this function)
autumn.c:563: error: 'autumnPaintOutput' undeclared (first use in this function)
autumn.c:564: error: 'drawWindow' undeclared (first use in this function)
autumn.c:564: error: 'autumnDrawWindow' undeclared (first use in this function)
autumn.c:566: error: dereferencing pointer to incomplete type
autumn.c:569: error: 'TRUE' undeclared (first use in this function)
autumn.c:570: warning: control reaches end of non-void function
autumn.c: In function 'autumnFiniScreen':
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:583: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:585: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:586: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:589: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:590: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:592: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:593: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:595: warning: implicit declaration of function 'UNWRAP'
autumn.c:595: warning: nested extern declaration of 'UNWRAP'
autumn.c:595: error: 'paintOutput' undeclared (first use in this function)
autumn.c:596: error: 'drawWindow' undeclared (first use in this function)
autumn.c: In function 'autumnDisplayOptionChanged':
autumn.c:606: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:617: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:617: error: 'TRUE' undeclared (first use in this function)
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:648: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:648: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:650: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:668: error: dereferencing pointer to incomplete type
autumn.c:669: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c: In function 'autumnInitDisplay':
autumn.c:689: warning: implicit declaration of function 'allocateScreenPrivateIndex'
autumn.c:689: warning: nested extern declaration of 'allocateScreenPrivateIndex'
autumn.c:693: error: 'FALSE' undeclared (first use in this function)
autumn.c:696: error: too many arguments to function 'autumnSetToggleInitiate'
autumn.c:703: error: dereferencing pointer to incomplete type
autumn.c:704: error: dereferencing pointer to incomplete type
autumn.c:706: error: dereferencing pointer to incomplete type
autumn.c:708: error: 'TRUE' undeclared (first use in this function)
autumn.c:709: warning: control reaches end of non-void function
autumn.c: In function 'autumnFiniDisplay':
autumn.c:715: error: dereferencing pointer to incomplete type
autumn.c:717: warning: implicit declaration of function 'freeScreenPrivateIndex'
autumn.c:717: warning: nested extern declaration of 'freeScreenPrivateIndex'
autumn.c: In function 'autumnInit':
autumn.c:724: warning: implicit declaration of function 'allocateDisplayPrivateIndex'
autumn.c:724: warning: nested extern declaration of 'allocateDisplayPrivateIndex'
autumn.c:726: error: 'FALSE' undeclared (first use in this function)
autumn.c:728: error: 'TRUE' undeclared (first use in this function)
autumn.c:729: warning: control reaches end of non-void function
autumn.c: In function 'autumnFini':
autumn.c:734: warning: implicit declaration of function 'freeDisplayPrivateIndex'
autumn.c:734: warning: nested extern declaration of 'freeDisplayPrivateIndex'
autumn.c: In function 'autumnGetVersion':
autumn.c:741: error: 'ABIVERSION' undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'autumnVTable'
autumn.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/autumn.lo] Error 1
Would you like to install the default background (the one shown on YouTube) (yes/no)?  
y

```

---

### Post by PatrickFisher on 2007-11-28
> **213374U said:**
> Ran the install. Everything seemed to go fine, asked me if I wanted to install default background, then no Advanced Desktop Effects showed up. Check the code out below and see if you can help me. Feisty user.

Thanks


It would seem that Feisty is not supported, since there is an error for every line of code in autumn.c

I'm sorry to say that there is no chance that I'll fix this. I'm on Gutsy and working on the Elements plugin, I guess we wait and see if that works on Feisty.

---

### Post by nandotron on 2007-11-29
Hi there,

I'm running the commands from the script one by one and here are the 2 problems I've hit so far:  it cannot find an installation candidate for the package 'gitweb' and also when i get to the command:

```
enda@enda-laptop:~/.autumn$ make
```

the output is:

```

convert   : autumn.xml.in -> build/autumn.xml
bcop'ing  : build/autumn.xml -> build/autumn_options.h
bcop'ing  : build/autumn.xml -> build/autumn_options.c
schema    : build/autumn.xml -> build/compiz-autumn.schema
make: *** No rule to make target `build/autumn.lo', needed by `c-build-objs'.  Stop.
```

something wrong in the makefile?

cheers!

---

### Post by nandotron on 2007-11-29
Ok,

finally got it, it all went wrong when I couldn't install the gitweb package - my repos were messed up.  once i installed that package everything was cool.  thanks a lot for your help guys!  Anyone know where I can come across some neat matching wallpaper?  I have a 1920x1200 monitor!

Thanks!

---

### Post by Takster on 2007-11-29
Awesome, it worked like a charm and looks great. Now i have to find a nice wallpaper. :)

Many thanks to the thread poster, well done!

---

### Post by aaaantoine on 2007-11-29
Fantastic plug-in, Pat!

Too bad I can only sensibly use it for another... 22 days or so.  Ah well, I'll check out Snow come winter. :)

---

### Post by Jay_Bee on 2007-11-29
Great work!
I love this plugin. Only problem I had was that it didn't install the background even though I typed yes so set it the image as background manually:KS

---

### Post by sdowney717 on 2007-11-29
yes very nice.
super plus F11 makes it run.

How do you know the key bindings?
In my compiz manager, I dont see any key bindings listed for any plugins.

I am using CompizConfig Settings Manager 0.5.2

---

### Post by PatrickFisher on 2007-11-29
> **sdowney717 said:**
> yes very nice.
super plus F11 makes it run.

How do you know the key bindings?
In my compiz manager, I dont see any key bindings listed for any plugins.

I am using CompizConfig Settings Manager 0.5.2

If you click the plugin, key bindings are in the last tab "Actions"

---

### Post by koleoptero on 2007-11-30
Thank you for this wonderful plugin. :) Don't stop here though, make one for every season :D

---

### Post by gfixler on 2007-12-01
I wanted to be sure and leave a comment that I installed this, and found it to be completely awesome! I didn't see it in your instructions, but I needed to restart X before on-the-fly changes to the settings in the CCSM would do anything. Maybe that's a Compiz install standard, but I'm a bit new to this stuff.. With that, it works perfectly, and I like the included options. Thanks!

---

### Post by Gourgi on 2007-12-07
Hi , gutsy version here with this (unofficial) git repository enabled 
>  [http://kwatrow.nl/repo](http://kwatrow.nl/repo) 
here are some version numbers
> 
Package	compiz-bcop_0.6.99+git20071021+Qubuntu0_amd64.deb
Package	compiz-dev_0.6.3+git20071119+Qubuntu0_amd64.deb


i ran the script , it didn;t work so i ran the lines of the script one by one
apt-get install ... packages  --> everything is installed 
so followed the lines (created dir autumn, sudo cp images ...)

here is the error output when i **make**
```
compiling : autumn.c -> build/autumn.loIn file included from autumn.c:43:
build/autumn_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:96: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:109: error: expected declaration specifiers or '...' before 'CompActionCallBackProc'
build/autumn_options.h:110: error: expected declaration specifiers or '...' before 'CompActionCallBackProc'
autumn.c:74: error: expected specifier-qualifier-list before 'CompTexture'
autumn.c:101: error: expected specifier-qualifier-list before 'PaintOutputProc'
autumn.c: In function 'autumnThink':
autumn.c:123: error: dereferencing pointer to incomplete type
autumn.c:125: error: dereferencing pointer to incomplete type
autumn.c:127: error: dereferencing pointer to incomplete type
autumn.c:128: error: dereferencing pointer to incomplete type
autumn.c:133: error: dereferencing pointer to incomplete type
autumn.c: In function 'stepLeafPositions':
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:160: error: 'TRUE' undeclared (first use in this function)
autumn.c:160: error: (Each undeclared identifier is reported only once
autumn.c:160: error: for each function it appears in.)
autumn.c:162: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:163: error: dereferencing pointer to incomplete type
autumn.c:164: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:175: error: dereferencing pointer to incomplete type
autumn.c:175: error: 'CompWindowTypeDesktopMask' undeclared (first use in this function)
autumn.c:176: warning: implicit declaration of function 'addWindowDamage'
autumn.c:176: warning: nested extern declaration of 'addWindowDamage'
autumn.c:180: warning: implicit declaration of function 'damageScreen'
autumn.c:180: warning: nested extern declaration of 'damageScreen'
autumn.c:183: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:187: error: expected declaration specifiers or '...' before 'CompAction'
autumn.c:188: error: expected declaration specifiers or '...' before 'CompActionState'
autumn.c: In function 'autumnToggle':
autumn.c:195: warning: implicit declaration of function 'getIntOptionNamed'
autumn.c:195: warning: nested extern declaration of 'getIntOptionNamed'
autumn.c:196: warning: implicit declaration of function 'findScreenAtDisplay'
autumn.c:196: warning: nested extern declaration of 'findScreenAtDisplay'
autumn.c:196: warning: assignment makes pointer from integer without a cast
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:206: error: 'TRUE' undeclared (first use in this function)
autumn.c:207: warning: control reaches end of non-void function
autumn.c: In function 'setupDisplayList':
autumn.c:231: error: dereferencing pointer to incomplete type
autumn.c:233: error: 'LeafScreen' has no member named 'displayList'
autumn.c:233: warning: implicit declaration of function 'glGenLists'
autumn.c:233: warning: nested extern declaration of 'glGenLists'
autumn.c:235: warning: implicit declaration of function 'glNewList'
autumn.c:235: warning: nested extern declaration of 'glNewList'
autumn.c:235: error: 'LeafScreen' has no member named 'displayList'
autumn.c:235: error: 'GL_COMPILE' undeclared (first use in this function)
autumn.c:236: warning: implicit declaration of function 'glBegin'
autumn.c:236: warning: nested extern declaration of 'glBegin'
autumn.c:236: error: 'GL_QUADS' undeclared (first use in this function)
autumn.c:238: warning: implicit declaration of function 'glColor4f'
autumn.c:238: warning: nested extern declaration of 'glColor4f'
autumn.c:239: warning: implicit declaration of function 'glVertex3f'
autumn.c:239: warning: nested extern declaration of 'glVertex3f'
autumn.c:247: warning: implicit declaration of function 'glEnd'
autumn.c:247: warning: nested extern declaration of 'glEnd'
autumn.c:248: warning: implicit declaration of function 'glEndList'
autumn.c:248: warning: nested extern declaration of 'glEndList'
autumn.c: In function 'beginRendering':
autumn.c:256: error: dereferencing pointer to incomplete type
autumn.c:257: warning: implicit declaration of function 'glEnable'
autumn.c:257: warning: nested extern declaration of 'glEnable'
autumn.c:257: error: 'GL_BLEND' undeclared (first use in this function)
autumn.c:259: warning: implicit declaration of function 'glTexEnvf'
autumn.c:259: warning: nested extern declaration of 'glTexEnvf'
autumn.c:259: error: 'GL_TEXTURE_ENV' undeclared (first use in this function)
autumn.c:259: error: 'GL_TEXTURE_ENV_MODE' undeclared (first use in this function)
autumn.c:259: error: 'GL_MODULATE' undeclared (first use in this function)
autumn.c:261: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:264: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:264: error: 'FALSE' undeclared (first use in this function)
autumn.c:268: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:268: error: dereferencing pointer to incomplete type
autumn.c:272: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:274: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:275: error: dereferencing pointer to incomplete type
autumn.c:276: error: dereferencing pointer to incomplete type
autumn.c:278: warning: implicit declaration of function 'enableTexture'
autumn.c:278: warning: nested extern declaration of 'enableTexture'
autumn.c:278: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:279: error: 'COMP_TEXTURE_FILTER_GOOD' undeclared (first use in this function)
autumn.c:283: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:285: warning: implicit declaration of function 'glTranslatef'
autumn.c:285: warning: nested extern declaration of 'glTranslatef'
autumn.c:288: warning: implicit declaration of function 'glRotatef'
autumn.c:288: warning: nested extern declaration of 'glRotatef'
autumn.c:289: warning: implicit declaration of function 'glCallList'
autumn.c:289: warning: nested extern declaration of 'glCallList'
autumn.c:289: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:300: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:306: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:314: warning: implicit declaration of function 'disableTexture'
autumn.c:314: warning: nested extern declaration of 'disableTexture'
autumn.c:314: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:319: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:320: error: dereferencing pointer to incomplete type
autumn.c:326: error: 'LeafScreen' has no member named 'displayList'
autumn.c:333: error: 'GL_REPLACE' undeclared (first use in this function)
autumn.c:334: error: dereferencing pointer to incomplete type
autumn.c:336: warning: implicit declaration of function 'glDisable'
autumn.c:336: warning: nested extern declaration of 'glDisable'
autumn.c:337: warning: implicit declaration of function 'glBlendFunc'
autumn.c:337: warning: nested extern declaration of 'glBlendFunc'
autumn.c:337: error: 'GL_ONE' undeclared (first use in this function)
autumn.c:337: error: 'GL_ONE_MINUS_SRC_ALPHA' undeclared (first use in this function)
autumn.c: At top level:
autumn.c:345: warning: type defaults to 'int' in declaration of 'ScreenPaintAttrib'
autumn.c:345: error: expected ';', ',' or ')' before '*' token
autumn.c:379: warning: type defaults to 'int' in declaration of 'CompTransform'
autumn.c:379: error: expected ';', ',' or ')' before '*' token
autumn.c: In function 'initiateLeaf':
autumn.c:407: error: dereferencing pointer to incomplete type
autumn.c:409: error: dereferencing pointer to incomplete type
autumn.c:412: error: dereferencing pointer to incomplete type
autumn.c:418: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:426: error: dereferencing pointer to incomplete type
autumn.c:432: error: dereferencing pointer to incomplete type
autumn.c:439: error: dereferencing pointer to incomplete type
autumn.c: In function 'setLeafTexture':
autumn.c:449: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:450: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:450: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c: In function 'updateLeafTextures':
autumn.c:457: error: dereferencing pointer to incomplete type
autumn.c:458: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:462: error: dereferencing pointer to incomplete type
autumn.c:464: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:466: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:468: warning: implicit declaration of function 'finiTexture'
autumn.c:468: warning: nested extern declaration of 'finiTexture'
autumn.c:468: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:469: warning: implicit declaration of function 'glDeleteLists'
autumn.c:469: warning: nested extern declaration of 'glDeleteLists'
autumn.c:469: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:472: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:473: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:474: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:476: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:480: error: 'CompMatrix' undeclared (first use in this function)
autumn.c:480: error: 'mat' undeclared (first use in this function)
autumn.c:483: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:484: warning: implicit declaration of function 'readImageToTexture'
autumn.c:484: warning: nested extern declaration of 'readImageToTexture'
autumn.c:484: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:485: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:485: error: dereferencing pointer to incomplete type
autumn.c:486: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:487: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:488: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:490: warning: implicit declaration of function 'compLogMessage'
autumn.c:490: warning: nested extern declaration of 'compLogMessage'
autumn.c:490: error: dereferencing pointer to incomplete type
autumn.c:490: error: 'CompLogLevelWarn' undeclared (first use in this function)
autumn.c:491: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:491: error: dereferencing pointer to incomplete type
autumn.c:494: error: dereferencing pointer to incomplete type
autumn.c:494: error: 'CompLogLevelInfo' undeclared (first use in this function)
autumn.c:495: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:495: error: dereferencing pointer to incomplete type
autumn.c:497: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:498: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:500: error: 'LeafTexture' has no member named 'dList'
autumn.c:501: error: 'LeafTexture' has no member named 'dList'
autumn.c:501: error: 'GL_COMPILE' undeclared (first use in this function)
autumn.c:503: error: 'GL_QUADS' undeclared (first use in this function)
autumn.c:505: warning: implicit declaration of function 'glTexCoord2f'
autumn.c:505: warning: nested extern declaration of 'glTexCoord2f'
autumn.c:505: warning: implicit declaration of function 'COMP_TEX_COORD_X'
autumn.c:505: warning: nested extern declaration of 'COMP_TEX_COORD_X'
autumn.c:505: warning: implicit declaration of function 'COMP_TEX_COORD_Y'
autumn.c:505: warning: nested extern declaration of 'COMP_TEX_COORD_Y'
autumn.c:506: warning: implicit declaration of function 'glVertex2f'
autumn.c:506: warning: nested extern declaration of 'glVertex2f'
autumn.c:508: error: 'LeafTexture' has no member named 'height'
autumn.c:509: error: 'LeafTexture' has no member named 'height'
autumn.c:509: error: 'LeafTexture' has no member named 'width'
autumn.c:510: error: 'LeafTexture' has no member named 'width'
autumn.c:511: error: 'LeafTexture' has no member named 'height'
autumn.c:512: error: 'LeafTexture' has no member named 'height'
autumn.c:512: error: 'LeafTexture' has no member named 'width'
autumn.c:513: error: 'LeafTexture' has no member named 'width'
autumn.c:523: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:525: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:525: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c: In function 'autumnInitScreen':
autumn.c:536: error: dereferencing pointer to incomplete type
autumn.c:539: error: dereferencing pointer to incomplete type
autumn.c:543: error: dereferencing pointer to incomplete type
autumn.c:546: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:547: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:548: error: 'FALSE' undeclared (first use in this function)
autumn.c:549: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:551: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:563: warning: implicit declaration of function 'WRAP'
autumn.c:563: warning: nested extern declaration of 'WRAP'
autumn.c:563: error: 'paintOutput' undeclared (first use in this function)
autumn.c:563: error: 'autumnPaintOutput' undeclared (first use in this function)
autumn.c:564: error: 'drawWindow' undeclared (first use in this function)
autumn.c:564: error: 'autumnDrawWindow' undeclared (first use in this function)
autumn.c:566: error: dereferencing pointer to incomplete type
autumn.c:569: error: 'TRUE' undeclared (first use in this function)
autumn.c:570: warning: control reaches end of non-void function
autumn.c: In function 'autumnFiniScreen':
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:583: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:585: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:586: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:589: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:590: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:592: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:593: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:595: warning: implicit declaration of function 'UNWRAP'
autumn.c:595: warning: nested extern declaration of 'UNWRAP'
autumn.c:595: error: 'paintOutput' undeclared (first use in this function)
autumn.c:596: error: 'drawWindow' undeclared (first use in this function)
autumn.c: In function 'autumnDisplayOptionChanged':
autumn.c:606: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:617: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:617: error: 'TRUE' undeclared (first use in this function)
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:648: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:648: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:650: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:668: error: dereferencing pointer to incomplete type
autumn.c:669: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c: In function 'autumnInitDisplay':
autumn.c:689: warning: implicit declaration of function 'allocateScreenPrivateIndex'
autumn.c:689: warning: nested extern declaration of 'allocateScreenPrivateIndex'
autumn.c:693: error: 'FALSE' undeclared (first use in this function)
autumn.c:696: error: too many arguments to function 'autumnSetToggleInitiate'
autumn.c:703: error: dereferencing pointer to incomplete type
autumn.c:704: error: dereferencing pointer to incomplete type
autumn.c:706: error: dereferencing pointer to incomplete type
autumn.c:708: error: 'TRUE' undeclared (first use in this function)
autumn.c:709: warning: control reaches end of non-void function
autumn.c: In function 'autumnFiniDisplay':
autumn.c:715: error: dereferencing pointer to incomplete type
autumn.c:717: warning: implicit declaration of function 'freeScreenPrivateIndex'
autumn.c:717: warning: nested extern declaration of 'freeScreenPrivateIndex'
autumn.c: In function 'autumnInit':
autumn.c:724: warning: implicit declaration of function 'allocateDisplayPrivateIndex'
autumn.c:724: warning: nested extern declaration of 'allocateDisplayPrivateIndex'
autumn.c:726: error: 'FALSE' undeclared (first use in this function)
autumn.c:728: error: 'TRUE' undeclared (first use in this function)
autumn.c:729: warning: control reaches end of non-void function
autumn.c: In function 'autumnFini':
autumn.c:734: warning: implicit declaration of function 'freeDisplayPrivateIndex'
autumn.c:734: warning: nested extern declaration of 'freeDisplayPrivateIndex'
autumn.c: In function 'autumnGetVersion':
autumn.c:741: error: 'ABIVERSION' undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'autumnVTable'
autumn.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/autumn.lo] Error 1
 
```
is this error caused because of the repo i use ?
if so, in order to make autumn work i have to downgrade to official repo
and run .sh again ?

thanks  in advance

btw great idea of put the "related" plugins (snow,stars) together!

---

### Post by jryprt on 2007-12-12
> **Jay_Bee said:**
> Great work!
I love this plugin. Only problem I had was that it didn't install the background even though I typed yes so set it the image as background manually:KS

Same here Very nice

---

### Post by ImAnOgre on 2008-02-18
PatrickFisher,
  Thanks a lot.  Flawless install and lots of eye candy now.

[img]http://student.claytonstate.net/~mstevenson3/yourawesome.gif[/img]

---

### Post by chavanak on 2008-02-18
This plugin is great!!! Better than the default snow plugin

---

### Post by noodles12 on 2008-02-26
THanks man, cherry blossoms is a dream come true!

Here' my tiny wishlist for if you're bored =) 
1. Can pick where on the screen and how large of an area the leaves originate from. 
2. Diagonal directions in the leaves
3. Can choose the strenght of the wind

---

### Post by jhenager on 2008-02-26
It seemed to install ok on the 64 bit version, but complained about too many fish. So I tried the Autumn plug in, and it is there, but no leaves. Maybe too close to spring.....

---

### Post by noodles12 on 2008-02-27
I know some of you have been asking so .....

...here are some cherry blossoms! 

made by coz_

---

### Post by RJ Hythloday on 2008-02-27
can't wait to get home and try it out! :KS

---

### Post by chunchengch on 2008-02-27
I am using Ubuntu 7.10 and compiz 0.7.1, and I run the script autumninstall.sh with command "sudo bash ./autumninstall.sh", but I also get the error message, so what is your suggestion? thanks a lot!



convert   : autumn.xml.in -> build/autumn.xml
bcop'ing  : build/autumn.xml -> build/autumn_options.h
bcop'ing  : build/autumn.xml -> build/autumn_options.c
schema    : build/autumn.xml -> build/compiz-autumn.schema
compiling : autumn.c -> build/autumn.loIn file included from autumn.c:43:
build/autumn_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:96: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:108: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/autumn_options.h:109: error: expected declaration specifiers or '...' before 'CompActionCallBackProc'
build/autumn_options.h:110: error: expected declaration specifiers or '...' before 'CompActionCallBackProc'
autumn.c:74: error: expected specifier-qualifier-list before 'CompTexture'
autumn.c:101: error: expected specifier-qualifier-list before 'PaintOutputProc'
autumn.c: In function 'autumnThink':
autumn.c:123: error: dereferencing pointer to incomplete type
autumn.c:125: error: dereferencing pointer to incomplete type
autumn.c:127: error: dereferencing pointer to incomplete type
autumn.c:128: error: dereferencing pointer to incomplete type
autumn.c:133: error: dereferencing pointer to incomplete type
autumn.c: In function 'stepLeafPositions':
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:160: error: 'TRUE' undeclared (first use in this function)
autumn.c:160: error: (Each undeclared identifier is reported only once
autumn.c:160: error: for each function it appears in.)
autumn.c:162: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:163: error: dereferencing pointer to incomplete type
autumn.c:164: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:175: error: dereferencing pointer to incomplete type
autumn.c:175: error: 'CompWindowTypeDesktopMask' undeclared (first use in this function)
autumn.c:176: warning: implicit declaration of function 'addWindowDamage'
autumn.c:176: warning: nested extern declaration of 'addWindowDamage'
autumn.c:180: warning: implicit declaration of function 'damageScreen'
autumn.c:180: warning: nested extern declaration of 'damageScreen'
autumn.c:183: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:187: error: expected declaration specifiers or '...' before 'CompAction'
autumn.c:188: error: expected declaration specifiers or '...' before 'CompActionState'
autumn.c: In function 'autumnToggle':
autumn.c:195: warning: implicit declaration of function 'getIntOptionNamed'
autumn.c:195: warning: nested extern declaration of 'getIntOptionNamed'
autumn.c:196: warning: implicit declaration of function 'findScreenAtDisplay'
autumn.c:196: warning: nested extern declaration of 'findScreenAtDisplay'
autumn.c:196: warning: assignment makes pointer from integer without a cast
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:206: error: 'TRUE' undeclared (first use in this function)
autumn.c:207: warning: control reaches end of non-void function
autumn.c: In function 'setupDisplayList':
autumn.c:231: error: dereferencing pointer to incomplete type
autumn.c:233: error: 'LeafScreen' has no member named 'displayList'
autumn.c:233: warning: implicit declaration of function 'glGenLists'
autumn.c:233: warning: nested extern declaration of 'glGenLists'
autumn.c:235: warning: implicit declaration of function 'glNewList'
autumn.c:235: warning: nested extern declaration of 'glNewList'
autumn.c:235: error: 'LeafScreen' has no member named 'displayList'
autumn.c:235: error: 'GL_COMPILE' undeclared (first use in this function)
autumn.c:236: warning: implicit declaration of function 'glBegin'
autumn.c:236: warning: nested extern declaration of 'glBegin'
autumn.c:236: error: 'GL_QUADS' undeclared (first use in this function)
autumn.c:238: warning: implicit declaration of function 'glColor4f'
autumn.c:238: warning: nested extern declaration of 'glColor4f'
autumn.c:239: warning: implicit declaration of function 'glVertex3f'
autumn.c:239: warning: nested extern declaration of 'glVertex3f'
autumn.c:247: warning: implicit declaration of function 'glEnd'
autumn.c:247: warning: nested extern declaration of 'glEnd'
autumn.c:248: warning: implicit declaration of function 'glEndList'
autumn.c:248: warning: nested extern declaration of 'glEndList'
autumn.c: In function 'beginRendering':
autumn.c:256: error: dereferencing pointer to incomplete type
autumn.c:257: warning: implicit declaration of function 'glEnable'
autumn.c:257: warning: nested extern declaration of 'glEnable'
autumn.c:257: error: 'GL_BLEND' undeclared (first use in this function)
autumn.c:259: warning: implicit declaration of function 'glTexEnvf'
autumn.c:259: warning: nested extern declaration of 'glTexEnvf'
autumn.c:259: error: 'GL_TEXTURE_ENV' undeclared (first use in this function)
autumn.c:259: error: 'GL_TEXTURE_ENV_MODE' undeclared (first use in this function)
autumn.c:259: error: 'GL_MODULATE' undeclared (first use in this function)
autumn.c:261: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:264: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:264: error: 'FALSE' undeclared (first use in this function)
autumn.c:268: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:268: error: dereferencing pointer to incomplete type
autumn.c:272: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:274: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:275: error: dereferencing pointer to incomplete type
autumn.c:276: error: dereferencing pointer to incomplete type
autumn.c:278: warning: implicit declaration of function 'enableTexture'
autumn.c:278: warning: nested extern declaration of 'enableTexture'
autumn.c:278: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:279: error: 'COMP_TEXTURE_FILTER_GOOD' undeclared (first use in this function)
autumn.c:283: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:285: warning: implicit declaration of function 'glTranslatef'
autumn.c:285: warning: nested extern declaration of 'glTranslatef'
autumn.c:288: warning: implicit declaration of function 'glRotatef'
autumn.c:288: warning: nested extern declaration of 'glRotatef'
autumn.c:289: warning: implicit declaration of function 'glCallList'
autumn.c:289: warning: nested extern declaration of 'glCallList'
autumn.c:289: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:300: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:306: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:314: warning: implicit declaration of function 'disableTexture'
autumn.c:314: warning: nested extern declaration of 'disableTexture'
autumn.c:314: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:319: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:320: error: dereferencing pointer to incomplete type
autumn.c:326: error: 'LeafScreen' has no member named 'displayList'
autumn.c:333: error: 'GL_REPLACE' undeclared (first use in this function)
autumn.c:334: error: dereferencing pointer to incomplete type
autumn.c:336: warning: implicit declaration of function 'glDisable'
autumn.c:336: warning: nested extern declaration of 'glDisable'
autumn.c:337: warning: implicit declaration of function 'glBlendFunc'
autumn.c:337: warning: nested extern declaration of 'glBlendFunc'
autumn.c:337: error: 'GL_ONE' undeclared (first use in this function)
autumn.c:337: error: 'GL_ONE_MINUS_SRC_ALPHA' undeclared (first use in this function)
autumn.c: At top level:
autumn.c:345: warning: type defaults to 'int' in declaration of 'ScreenPaintAttrib'
autumn.c:345: error: expected ';', ',' or ')' before '*' token
autumn.c:379: warning: type defaults to 'int' in declaration of 'CompTransform'
autumn.c:379: error: expected ';', ',' or ')' before '*' token
autumn.c: In function 'initiateLeaf':
autumn.c:407: error: dereferencing pointer to incomplete type
autumn.c:409: error: dereferencing pointer to incomplete type
autumn.c:412: error: dereferencing pointer to incomplete type
autumn.c:418: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:426: error: dereferencing pointer to incomplete type
autumn.c:432: error: dereferencing pointer to incomplete type
autumn.c:439: error: dereferencing pointer to incomplete type
autumn.c: In function 'setLeafTexture':
autumn.c:449: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:450: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:450: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c: In function 'updateLeafTextures':
autumn.c:457: error: dereferencing pointer to incomplete type
autumn.c:458: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:462: error: dereferencing pointer to incomplete type
autumn.c:464: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:466: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:468: warning: implicit declaration of function 'finiTexture'
autumn.c:468: warning: nested extern declaration of 'finiTexture'
autumn.c:468: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:469: warning: implicit declaration of function 'glDeleteLists'
autumn.c:469: warning: nested extern declaration of 'glDeleteLists'
autumn.c:469: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:472: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:473: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:474: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:476: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:480: error: 'CompMatrix' undeclared (first use in this function)
autumn.c:480: error: 'mat' undeclared (first use in this function)
autumn.c:483: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:484: warning: implicit declaration of function 'readImageToTexture'
autumn.c:484: warning: nested extern declaration of 'readImageToTexture'
autumn.c:484: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:485: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:485: error: dereferencing pointer to incomplete type
autumn.c:486: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:487: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:488: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:490: warning: implicit declaration of function 'compLogMessage'
autumn.c:490: warning: nested extern declaration of 'compLogMessage'
autumn.c:490: error: dereferencing pointer to incomplete type
autumn.c:490: error: 'CompLogLevelWarn' undeclared (first use in this function)
autumn.c:491: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:491: error: dereferencing pointer to incomplete type
autumn.c:494: error: dereferencing pointer to incomplete type
autumn.c:494: error: 'CompLogLevelInfo' undeclared (first use in this function)
autumn.c:495: error: invalid use of undefined type 'union _CompOptionValue'
autumn.c:495: error: dereferencing pointer to incomplete type
autumn.c:497: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:498: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:500: error: 'LeafTexture' has no member named 'dList'
autumn.c:501: error: 'LeafTexture' has no member named 'dList'
autumn.c:501: error: 'GL_COMPILE' undeclared (first use in this function)
autumn.c:503: error: 'GL_QUADS' undeclared (first use in this function)
autumn.c:505: warning: implicit declaration of function 'glTexCoord2f'
autumn.c:505: warning: nested extern declaration of 'glTexCoord2f'
autumn.c:505: warning: implicit declaration of function 'COMP_TEX_COORD_X'
autumn.c:505: warning: nested extern declaration of 'COMP_TEX_COORD_X'
autumn.c:505: warning: implicit declaration of function 'COMP_TEX_COORD_Y'
autumn.c:505: warning: nested extern declaration of 'COMP_TEX_COORD_Y'
autumn.c:506: warning: implicit declaration of function 'glVertex2f'
autumn.c:506: warning: nested extern declaration of 'glVertex2f'
autumn.c:508: error: 'LeafTexture' has no member named 'height'
autumn.c:509: error: 'LeafTexture' has no member named 'height'
autumn.c:509: error: 'LeafTexture' has no member named 'width'
autumn.c:510: error: 'LeafTexture' has no member named 'width'
autumn.c:511: error: 'LeafTexture' has no member named 'height'
autumn.c:512: error: 'LeafTexture' has no member named 'height'
autumn.c:512: error: 'LeafTexture' has no member named 'width'
autumn.c:513: error: 'LeafTexture' has no member named 'width'
autumn.c:523: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:525: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:525: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c: In function 'autumnInitScreen':
autumn.c:536: error: dereferencing pointer to incomplete type
autumn.c:539: error: dereferencing pointer to incomplete type
autumn.c:543: error: dereferencing pointer to incomplete type
autumn.c:546: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:547: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:548: error: 'FALSE' undeclared (first use in this function)
autumn.c:549: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:551: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:563: warning: implicit declaration of function 'WRAP'
autumn.c:563: warning: nested extern declaration of 'WRAP'
autumn.c:563: error: 'paintOutput' undeclared (first use in this function)
autumn.c:563: error: 'autumnPaintOutput' undeclared (first use in this function)
autumn.c:564: error: 'drawWindow' undeclared (first use in this function)
autumn.c:564: error: 'autumnDrawWindow' undeclared (first use in this function)
autumn.c:566: error: dereferencing pointer to incomplete type
autumn.c:569: error: 'TRUE' undeclared (first use in this function)
autumn.c:570: warning: control reaches end of non-void function
autumn.c: In function 'autumnFiniScreen':
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:583: error: 'LeafScreen' has no member named 'autumnTexturesLoaded'
autumn.c:585: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:586: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:589: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:590: error: 'LeafScreen' has no member named 'autumnTex'
autumn.c:592: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:593: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:595: warning: implicit declaration of function 'UNWRAP'
autumn.c:595: warning: nested extern declaration of 'UNWRAP'
autumn.c:595: error: 'paintOutput' undeclared (first use in this function)
autumn.c:596: error: 'drawWindow' undeclared (first use in this function)
autumn.c: In function 'autumnDisplayOptionChanged':
autumn.c:606: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:617: error: 'LeafScreen' has no member named 'displayListNeedsUpdate'
autumn.c:617: error: 'TRUE' undeclared (first use in this function)
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:648: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:648: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:650: error: 'LeafScreen' has no member named 'allLeaves'
autumn.c:668: error: dereferencing pointer to incomplete type
autumn.c:669: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c: In function 'autumnInitDisplay':
autumn.c:689: warning: implicit declaration of function 'allocateScreenPrivateIndex'
autumn.c:689: warning: nested extern declaration of 'allocateScreenPrivateIndex'
autumn.c:693: error: 'FALSE' undeclared (first use in this function)
autumn.c:696: error: too many arguments to function 'autumnSetToggleInitiate'
autumn.c:703: error: dereferencing pointer to incomplete type
autumn.c:704: error: dereferencing pointer to incomplete type
autumn.c:706: error: dereferencing pointer to incomplete type
autumn.c:708: error: 'TRUE' undeclared (first use in this function)
autumn.c:709: warning: control reaches end of non-void function
autumn.c: In function 'autumnFiniDisplay':
autumn.c:715: error: dereferencing pointer to incomplete type
autumn.c:717: warning: implicit declaration of function 'freeScreenPrivateIndex'
autumn.c:717: warning: nested extern declaration of 'freeScreenPrivateIndex'
autumn.c: In function 'autumnInit':
autumn.c:724: warning: implicit declaration of function 'allocateDisplayPrivateIndex'
autumn.c:724: warning: nested extern declaration of 'allocateDisplayPrivateIndex'
autumn.c:726: error: 'FALSE' undeclared (first use in this function)
autumn.c:728: error: 'TRUE' undeclared (first use in this function)
autumn.c:729: warning: control reaches end of non-void function
autumn.c: In function 'autumnFini':
autumn.c:734: warning: implicit declaration of function 'freeDisplayPrivateIndex'
autumn.c:734: warning: nested extern declaration of 'freeDisplayPrivateIndex'
autumn.c: In function 'autumnGetVersion':
autumn.c:741: error: 'ABIVERSION' undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'autumnVTable'
autumn.c:762: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/autumn.lo] Error 1

---

### Post by ralbas on 2008-03-12
Gracias por el plugin, tenia tiempo buscandolo.

Saludos desde mexico

---

### Post by bro on 2008-03-26
I just get white blocks on the screen instead of leaves. Why is that?

by the way @ chunchengch: could you past such long stuff in an attachment?

---

### Post by ADBD on 2008-03-27
installation doesn't work. there's lots of text and then: 
Get:5 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main libxi-dev 2:1.1.2-1 [68.9kB]
Get:6 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main m4 1.4.10-0ubuntu2 [207kB]
Get:7 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main autoconf 2.61-4 [448kB]
Get:8 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main autotools-dev 20070306.1 [61.6kB]
Get:9 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main automake 1:1.10+nogfdl-1 [369kB]
Get:10 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main automake1.9 1.9.6+nogfdl-3ubuntu1 [388kB]
Get:11 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main libcurl3 7.16.4-2ubuntu1 [182kB]
Get:12 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) gutsy/main curl 7.16.4-2ubuntu1 [175kB]
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

well i put on the cd and it installed but it doesn't work. the leaves just won't appear

---

### Post by abhishekrd on 2008-03-27
omg after 30mins of finding the directory i got it up and running!!! thanks!!

it was so easy but i made it difficult :):):)

---

### Post by Trail on 2008-03-28
Awesome.

---

### Post by Zeroc00l on 2008-03-30
hi guyz, I just upgraded to ubuntu 8.04, with compiz fusion 0.7.2, now I have a problem with Autumn Plugin, it doesn't seem to recognize the settings of the new Compiz, I editedthe .xml file to make appear the options on the Compiz Settings Manager, but nothing seems to function.

Perhaps some things has changed on Compiz 0.7.2 but I saw the code of autumn.c and really i don't know where to edit this file, I suppose that I must change the Initiate command to make the read from the .xml function. howevere anybody knows how to trick this problem?

thanks guyz for the answers! bye bye!

---

### Post by Sitar on 2008-04-04
Thank you very much :) I am completely new to Linux, but the installation went flawless :D it looks pretty!

---

### Post by JoLiSh on 2008-04-05
It's not Autumn any more, so I made some appearance changes.
I just used the settings menu of this plug-in to bring a little spring of spring to my desktop.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=65025&stc=1&d=1207417678[/IMG]

The changes are:
[LIST]
[*]change textures of leaves to bees. (I attached them to this message)
[*]add left wind.
[*]increase number of leaves.
[*]decrease size of leaves.
[*]increase leaf speed.
[*]disable rotate leaves.
[*]change background to a flower field.
[/LIST]

And that's all of it.
Do you like it?
:lolflag:

---

### Post by ZarathustraDK on 2008-04-22
Nice work!

If I could wish for something it'd be a sakura-hana plugin.
[http://en.wikipedia.org/wiki/Sakura#Symbolism](http://en.wikipedia.org/wiki/Sakura#Symbolism)

Yeh, I'm a japanophile, what can I say :)

---

### Post by Khuezy on 2008-05-01
autumn.c:734: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
autumn.c:734: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
autumn.c: In function ‘autumnGetVersion’:
autumn.c:741: error: ‘ABIVERSION’ undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘autumnVTable’
autumn.c:762: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/autumn.lo] Error 1
compiling : autumn.c -> build/autumn.loIn file included from autumn.c:43:
build/autumn_options.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/autumn_options.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/autumn_options.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
build/autumn_options.h:109: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
build/autumn_options.h:110: error: expected declaration specifiers or ‘...’ before ‘CompActionCallBackProc’
autumn.c:74: error: expected specifier-qualifier-list before ‘CompTexture’
autumn.c:101: error: expected specifier-qualifier-list before ‘PaintOutputProc’
autumn.c: In function ‘autumnThink’:
autumn.c:123: error: dereferencing pointer to incomplete type
autumn.c:125: error: dereferencing pointer to incomplete type
autumn.c:127: error: dereferencing pointer to incomplete type
autumn.c:128: error: dereferencing pointer to incomplete type
autumn.c:133: error: dereferencing pointer to incomplete type
autumn.c: In function ‘stepLeafPositions’:
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:157: error: dereferencing pointer to incomplete type
autumn.c:160: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:160: error: (Each undeclared identifier is reported only once
autumn.c:160: error: for each function it appears in.)
autumn.c:162: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:163: error: dereferencing pointer to incomplete type
autumn.c:164: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:173: error: dereferencing pointer to incomplete type
autumn.c:175: error: dereferencing pointer to incomplete type
autumn.c:175: error: ‘CompWindowTypeDesktopMask’ undeclared (first use in this function)
autumn.c:176: warning: implicit declaration of function ‘addWindowDamage’
autumn.c:176: warning: nested extern declaration of ‘addWindowDamage’
autumn.c:180: warning: implicit declaration of function ‘damageScreen’
autumn.c:180: warning: nested extern declaration of ‘damageScreen’
autumn.c:183: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:187: error: expected declaration specifiers or ‘...’ before ‘CompAction’
autumn.c:188: error: expected declaration specifiers or ‘...’ before ‘CompActionState’
autumn.c: In function ‘autumnToggle’:
autumn.c:195: warning: implicit declaration of function ‘getIntOptionNamed’
autumn.c:195: warning: nested extern declaration of ‘getIntOptionNamed’
autumn.c:196: warning: implicit declaration of function ‘findScreenAtDisplay’
autumn.c:196: warning: nested extern declaration of ‘findScreenAtDisplay’
autumn.c:196: warning: assignment makes pointer from integer without a cast
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:200: error: dereferencing pointer to incomplete type
autumn.c:206: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:207: warning: control reaches end of non-void function
autumn.c: In function ‘setupDisplayList’:
autumn.c:231: error: dereferencing pointer to incomplete type
autumn.c:233: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:233: warning: implicit declaration of function ‘glGenLists’
autumn.c:233: warning: nested extern declaration of ‘glGenLists’
autumn.c:235: warning: implicit declaration of function ‘glNewList’
autumn.c:235: warning: nested extern declaration of ‘glNewList’
autumn.c:235: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:235: error: ‘GL_COMPILE’ undeclared (first use in this function)
autumn.c:236: warning: implicit declaration of function ‘glBegin’
autumn.c:236: warning: nested extern declaration of ‘glBegin’
autumn.c:236: error: ‘GL_QUADS’ undeclared (first use in this function)
autumn.c:238: warning: implicit declaration of function ‘glColor4f’
autumn.c:238: warning: nested extern declaration of ‘glColor4f’
autumn.c:239: warning: implicit declaration of function ‘glVertex3f’
autumn.c:239: warning: nested extern declaration of ‘glVertex3f’
autumn.c:247: warning: implicit declaration of function ‘glEnd’
autumn.c:247: warning: nested extern declaration of ‘glEnd’
autumn.c:248: warning: implicit declaration of function ‘glEndList’
autumn.c:248: warning: nested extern declaration of ‘glEndList’
autumn.c: In function ‘beginRendering’:
autumn.c:256: error: dereferencing pointer to incomplete type
autumn.c:257: warning: implicit declaration of function ‘glEnable’
autumn.c:257: warning: nested extern declaration of ‘glEnable’
autumn.c:257: error: ‘GL_BLEND’ undeclared (first use in this function)
autumn.c:259: warning: implicit declaration of function ‘glTexEnvf’
autumn.c:259: warning: nested extern declaration of ‘glTexEnvf’
autumn.c:259: error: ‘GL_TEXTURE_ENV’ undeclared (first use in this function)
autumn.c:259: error: ‘GL_TEXTURE_ENV_MODE’ undeclared (first use in this function)
autumn.c:259: error: ‘GL_MODULATE’ undeclared (first use in this function)
autumn.c:261: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:264: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:264: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:268: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:268: error: dereferencing pointer to incomplete type
autumn.c:272: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:274: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:275: error: dereferencing pointer to incomplete type
autumn.c:276: error: dereferencing pointer to incomplete type
autumn.c:278: warning: implicit declaration of function ‘enableTexture’
autumn.c:278: warning: nested extern declaration of ‘enableTexture’
autumn.c:278: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:279: error: ‘COMP_TEXTURE_FILTER_GOOD’ undeclared (first use in this function)
autumn.c:283: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:285: warning: implicit declaration of function ‘glTranslatef’
autumn.c:285: warning: nested extern declaration of ‘glTranslatef’
autumn.c:288: warning: implicit declaration of function ‘glRotatef’
autumn.c:288: warning: nested extern declaration of ‘glRotatef’
autumn.c:289: warning: implicit declaration of function ‘glCallList’
autumn.c:289: warning: nested extern declaration of ‘glCallList’
autumn.c:289: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:300: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:306: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:314: warning: implicit declaration of function ‘disableTexture’
autumn.c:314: warning: nested extern declaration of ‘disableTexture’
autumn.c:314: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:319: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:320: error: dereferencing pointer to incomplete type
autumn.c:326: error: ‘LeafScreen’ has no member named ‘displayList’
autumn.c:333: error: ‘GL_REPLACE’ undeclared (first use in this function)
autumn.c:334: error: dereferencing pointer to incomplete type
autumn.c:336: warning: implicit declaration of function ‘glDisable’
autumn.c:336: warning: nested extern declaration of ‘glDisable’
autumn.c:337: warning: implicit declaration of function ‘glBlendFunc’
autumn.c:337: warning: nested extern declaration of ‘glBlendFunc’
autumn.c:337: error: ‘GL_ONE’ undeclared (first use in this function)
autumn.c:337: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
autumn.c: At top level:
autumn.c:345: warning: type defaults to ‘int’ in declaration of ‘ScreenPaintAttrib’
autumn.c:345: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
autumn.c:379: warning: type defaults to ‘int’ in declaration of ‘CompTransform’
autumn.c:379: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
autumn.c: In function ‘initiateLeaf’:
autumn.c:407: error: dereferencing pointer to incomplete type
autumn.c:409: error: dereferencing pointer to incomplete type
autumn.c:412: error: dereferencing pointer to incomplete type
autumn.c:418: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:420: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:424: error: dereferencing pointer to incomplete type
autumn.c:426: error: dereferencing pointer to incomplete type
autumn.c:432: error: dereferencing pointer to incomplete type
autumn.c:439: error: dereferencing pointer to incomplete type
autumn.c: In function ‘setLeafTexture’:
autumn.c:449: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:450: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:450: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c: In function ‘updateLeafTextures’:
autumn.c:457: error: dereferencing pointer to incomplete type
autumn.c:458: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:461: error: dereferencing pointer to incomplete type
autumn.c:462: error: dereferencing pointer to incomplete type
autumn.c:464: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:466: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:468: warning: implicit declaration of function ‘finiTexture’
autumn.c:468: warning: nested extern declaration of ‘finiTexture’
autumn.c:468: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:469: warning: implicit declaration of function ‘glDeleteLists’
autumn.c:469: warning: nested extern declaration of ‘glDeleteLists’
autumn.c:469: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:472: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:473: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:474: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:476: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:480: error: ‘CompMatrix’ undeclared (first use in this function)
autumn.c:480: error: ‘mat’ undeclared (first use in this function)
autumn.c:483: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:484: warning: implicit declaration of function ‘readImageToTexture’
autumn.c:484: warning: nested extern declaration of ‘readImageToTexture’
autumn.c:484: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:485: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:485: error: dereferencing pointer to incomplete type
autumn.c:486: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:487: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:488: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:490: warning: implicit declaration of function ‘compLogMessage’
autumn.c:490: warning: nested extern declaration of ‘compLogMessage’
autumn.c:490: error: dereferencing pointer to incomplete type
autumn.c:490: error: ‘CompLogLevelWarn’ undeclared (first use in this function)
autumn.c:491: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:491: error: dereferencing pointer to incomplete type
autumn.c:494: error: dereferencing pointer to incomplete type
autumn.c:494: error: ‘CompLogLevelInfo’ undeclared (first use in this function)
autumn.c:495: error: invalid use of undefined type ‘union _CompOptionValue’
autumn.c:495: error: dereferencing pointer to incomplete type
autumn.c:497: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:498: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:500: error: ‘LeafTexture’ has no member named ‘dList’
autumn.c:501: error: ‘LeafTexture’ has no member named ‘dList’
autumn.c:501: error: ‘GL_COMPILE’ undeclared (first use in this function)
autumn.c:503: error: ‘GL_QUADS’ undeclared (first use in this function)
autumn.c:505: warning: implicit declaration of function ‘glTexCoord2f’
autumn.c:505: warning: nested extern declaration of ‘glTexCoord2f’
autumn.c:505: warning: implicit declaration of function ‘COMP_TEX_COORD_X’
autumn.c:505: warning: nested extern declaration of ‘COMP_TEX_COORD_X’
autumn.c:505: warning: implicit declaration of function ‘COMP_TEX_COORD_Y’
autumn.c:505: warning: nested extern declaration of ‘COMP_TEX_COORD_Y’
autumn.c:506: warning: implicit declaration of function ‘glVertex2f’
autumn.c:506: warning: nested extern declaration of ‘glVertex2f’
autumn.c:508: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:509: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:509: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:510: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:511: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:512: error: ‘LeafTexture’ has no member named ‘height’
autumn.c:512: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:513: error: ‘LeafTexture’ has no member named ‘width’
autumn.c:523: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:525: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:525: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c: In function ‘autumnInitScreen’:
autumn.c:536: error: dereferencing pointer to incomplete type
autumn.c:539: error: dereferencing pointer to incomplete type
autumn.c:543: error: dereferencing pointer to incomplete type
autumn.c:546: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:547: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:548: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:549: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:551: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:563: warning: implicit declaration of function ‘WRAP’
autumn.c:563: warning: nested extern declaration of ‘WRAP’
autumn.c:563: error: ‘paintOutput’ undeclared (first use in this function)
autumn.c:563: error: ‘autumnPaintOutput’ undeclared (first use in this function)
autumn.c:564: error: ‘drawWindow’ undeclared (first use in this function)
autumn.c:564: error: ‘autumnDrawWindow’ undeclared (first use in this function)
autumn.c:566: error: dereferencing pointer to incomplete type
autumn.c:569: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:570: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFiniScreen’:
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:578: error: dereferencing pointer to incomplete type
autumn.c:583: error: ‘LeafScreen’ has no member named ‘autumnTexturesLoaded’
autumn.c:585: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:586: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:589: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:590: error: ‘LeafScreen’ has no member named ‘autumnTex’
autumn.c:592: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:593: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:595: warning: implicit declaration of function ‘UNWRAP’
autumn.c:595: warning: nested extern declaration of ‘UNWRAP’
autumn.c:595: error: ‘paintOutput’ undeclared (first use in this function)
autumn.c:596: error: ‘drawWindow’ undeclared (first use in this function)
autumn.c: In function ‘autumnDisplayOptionChanged’:
autumn.c:606: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:614: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:616: error: dereferencing pointer to incomplete type
autumn.c:617: error: ‘LeafScreen’ has no member named ‘displayListNeedsUpdate’
autumn.c:617: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:626: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:628: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:645: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:647: error: dereferencing pointer to incomplete type
autumn.c:648: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:648: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:650: error: ‘LeafScreen’ has no member named ‘allLeaves’
autumn.c:668: error: dereferencing pointer to incomplete type
autumn.c:669: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c:671: error: dereferencing pointer to incomplete type
autumn.c: In function ‘autumnInitDisplay’:
autumn.c:689: warning: implicit declaration of function ‘allocateScreenPrivateIndex’
autumn.c:689: warning: nested extern declaration of ‘allocateScreenPrivateIndex’
autumn.c:693: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:696: error: too many arguments to function ‘autumnSetToggleInitiate’
autumn.c:703: error: dereferencing pointer to incomplete type
autumn.c:704: error: dereferencing pointer to incomplete type
autumn.c:706: error: dereferencing pointer to incomplete type
autumn.c:708: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:709: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFiniDisplay’:
autumn.c:715: error: dereferencing pointer to incomplete type
autumn.c:717: warning: implicit declaration of function ‘freeScreenPrivateIndex’
autumn.c:717: warning: nested extern declaration of ‘freeScreenPrivateIndex’
autumn.c: In function ‘autumnInit’:
autumn.c:724: warning: implicit declaration of function ‘allocateDisplayPrivateIndex’
autumn.c:724: warning: nested extern declaration of ‘allocateDisplayPrivateIndex’
autumn.c:726: error: ‘FALSE’ undeclared (first use in this function)
autumn.c:728: error: ‘TRUE’ undeclared (first use in this function)
autumn.c:729: warning: control reaches end of non-void function
autumn.c: In function ‘autumnFini’:
autumn.c:734: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
autumn.c:734: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
autumn.c: In function ‘autumnGetVersion’:
autumn.c:741: error: ‘ABIVERSION’ undeclared (first use in this function)
autumn.c:742: warning: control reaches end of non-void function
autumn.c: At top level:
autumn.c:744: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘autumnVTable’
autumn.c:762: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/autumn.lo] Error 1
Would you like to install the default background (the one shown on YouTube) (yes/no)?  
no


help?

---

### Post by norfair on 2008-05-02
Okay, I've downloaded the two files and ran the terminal code, but am not sure where to go from here. Upon running the terminal command a huge bunch of code appeared with things downloading left and right. I said yes to everything (includeding background image), as I assumed I was supposed to, and then it finished successfully. However, the effect is not listed in 'Advanced Desktop Effects.' Do I need to cut and paste these two files within a Compiz plugin folder somewhere in the files system in order for it to be recognized? It did I do something wrong at the start of this? Perhaps it's not workable in 8.04? Perhaps I'm just an idiot? Beats me!

---

### Post by khunmoung on 2008-05-05
All installation process underwent uneventfully on Ubuntu Hardy but
I also have experienced such problem mentioned in post #104 [http://ubuntuforums.org/showpost.php?p=4856858&postcount=104]("http://ubuntuforums.org/showpost.php?p=4856858&postcount=104")  :(
I 'm very willing to use that plug in but...how can I solve it...plz tell somebody....
Thanks in advance

---

### Post by redserpent7 on 2008-05-09
Same here... got the same error as in post 104......... why?? any suggestions?? help!!!

---

### Post by cidboy on 2008-05-20
I've just tried to install this package and when i typed in the code into the terminal, it came out with a bunch of error message. What am i doing wrong? (the files were in the right directory)

---

### Post by PatrickFisher on 2008-05-20
> **cidboy said:**
> I've just tried to install this package and when i typed in the code into the terminal, it came out with a bunch of error message. What am i doing wrong? (the files were in the right directory)

The plugin does not work with the newest version of Compiz. Stay tuned, there is something better coming.

---

### Post by Cyrus_Zei on 2008-06-15
okej i am just so ******* sick and tired of ******* tutorials that you can't *******  write

go to system->pref->advanced desktop effect and then WHAT!!! there are like 10000000 ******* effects IF you are gonna write on ******* tutorial write the whole thing, saying go and enable the damm plugin ain't gonna happen. S

SO if you PLEASE could help me and tell me what the **** the plugin is called cuz i have been trying with this **** for like 5 days now!!!!!!!!KILL ME

---

### Post by PatrickFisher on 2008-06-15
> **Cyrus_Zei said:**
> okej i am just so ******* sick and tired of ******* tutorials that you can't *******  write

go to system->pref->advanced desktop effect and then WHAT!!! there are like 10000000 ******* effects IF you are gonna write on ******* tutorial write the whole thing, saying go and enable the damm plugin ain't gonna happen. S

SO if you PLEASE could help me and tell me what the **** the plugin is called cuz i have been trying with this **** for like 5 days now!!!!!!!!KILL ME


Instead of swearing at me, READ THE WHOLE THING. (same goes for this post)
First of all, you'd have to INSTALL the plugin, THEN go to Desktop Effects, and then it shows up under... Oh my god, you guessed it (or not) "Autumn"! No kidding.

Anyways, next time don't be so damn rude.

Autumn does not work with the newest version of Compiz. If you're on 8.04 Hardy Heron, you'll want "Elements" instead. You can get it at:

[http://www.elementsplugin.com]("http://www.elementsplugin.com")

Elements shows up under the plugin name "Elements" once it's install. Huh.

Elements does not work on 7.10 Gutsy.

---

### Post by Cyrus_Zei on 2008-06-15
So sorry but i have sort off tried this like for a week now an really did read all the things and check everything but nothing, I didn't eaven got the bakground so I did edit it and put it the myself, but still nothing. Good tut but it didn't helped me out for some reason so nothing works

and once again so sorry for letting the anger get out over you. had a bad day. nice plugin btw saw the video and stuffs

---

### Post by PatrickFisher on 2008-06-15
> **Cyrus_Zei said:**
> So sorry but i have sort off tried this like for a week now an really did read all the things and check everything but nothing, I didn't eaven got the bakground so I did edit it and put it the myself, but still nothing. Good tut but it didn't helped me out for some reason so nothing works

and once again so sorry for letting the anger get out over you. had a bad day. nice plugin btw saw the video and stuffs

Are you on Ubuntu Hardy Heron??

---

### Post by Cyrus_Zei on 2008-06-15
yeah?

---

### Post by PatrickFisher on 2008-06-15
> **Cyrus_Zei said:**
> yeah?

Ok, as I said, Autumn DOES NOT WORK on Hardy Heron. Try Elements.

Elements INCLUDES an updated version of Autumn.

---

### Post by Cyrus_Zei on 2008-06-15
*hit myself*

it works now

*hit myself again*

thx m8

---

