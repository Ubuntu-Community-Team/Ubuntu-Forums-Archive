---
title: "Changing icon size in Unity 2d Ubuntu 12.04"
date: 2012-03-19
forum: Desktop Environments
---

### Post by bonzini on 2012-03-19
Hello all;

I have an older Toshiba laptop which will not run Unity 3d and is right now letting me try out 12.04.

I spent some time this weekend figuring out how to edit the .qml files to allow a smaller set of icons and therefore more of them in the launcher, and I thought I'd offer the changes here for anyone else interested.

Note that there is the possibility of screwing up the Unity 2d environment by editing the .qml files so if you decide to try this, you should make a backup (copy the files in question with a different name before you edit, for example) and of course be very careful!

You have to be comfortable with editing files as superuser.  Personally I prefer to use the terminal, shell and vi.  You may prefer a different set of alternatives.

Also, some of the line numbers below could change as the beta process continues, so don't just blindly make changes; take a look at what you are changing to ensure that it makes sense! (this is why this is not posted as a patch)

First, all of the .qml files live in /usr/share/unity-2d/shell.  You will change three files, as follows.

In that directory you will see a file called "Shell.qml".  In it you will adjust the width of the launcher, by changing line 47, which looks like

```
width: 65
```

to look like

```
width: 50
```

Then in the subdirectory "common", you will see a file called "IconTile.qml".  In it you will adjust the width and height of the main icon of the tile, by changing lines 71 and 72, which look like

```
sourceSize.width: 48
sourceSize.height: 48
```

to look like

```
sourceSize.width: 32
sourceSize.height: 32
```

Finally, in the subdirectory "launcher", you will see a file called "LauncherList.qml".  In it you will adjust the tile size by changing line 30, which looks like

```
property int tileSize: 54
```

to look like

```
property int tileSize: 38
```

and also the selection outline size by changing line 34, which says

```
property int selectionOutlineSize: 65
```

to say

```
property int selectionOutlineSize: 50
```

Now you need to check, and possibly change, one last thing.  In the same "launcher" directory, examine line 250 in the file "LauncherItem.qml".  If it looks like

```
width: 32
```

you are good to go.  On the other hand, it may show a width of some other (larger?) number.  If so, change it to 32.  The reason I am uncertain about this is that I was experimenting with a Unity editing tool before I rolled up my sleeves and dived in here and I think it may have changed this line for me.

That's it.  You now need to restart Unity-2d e.g. by logging out and logging back in again.

The only thing that is not quite right in this configuration is the workspace chooser icon which is a bit fat for its button.

If for some reason this doesn't work for you, I'd be interested in finding out what happened.  And remember, those backup versions of the .qml files you edited...

---

### Post by 3Miro on 2012-03-19
I thought in 12.04 you can change the Icon size from the Desktop menu. Right-click on the desktop and try to change the wallpaper, you should have an option for the Unity icons. Does this work for Unity 3D only?

---

### Post by bonzini on 2012-03-19
> **3Miro said:**
> I thought in 12.04 you can change the Icon size from the Desktop menu. Right-click on the desktop and try to change the wallpaper, you should have an option for the Unity icons. Does this work for Unity 3D only?

The size-changing is only offered, and only works in any case, in Unity 3D.

There are some similar instructions to mine "out there" for earlier versions but it seems Unity 2D is pretty fluid and fast moving.  I sort of feel like looking at Unity 2D on 11.10 to see if I can get that working too but only sort of.

---

### Post by 3Miro on 2012-03-20
> **bonzini said:**
> The size-changing is only offered, and only works in any case, in Unity 3D.

There are some similar instructions to mine "out there" for earlier versions but it seems Unity 2D is pretty fluid and fast moving.  I sort of feel like looking at Unity 2D on 11.10 to see if I can get that working too but only sort of.

I thought they had them both finally, I guess not. Thanks for the info.

---

### Post by bonzini on 2012-03-21
Updated QML files arrived today, and some changes in line numbers.

The change in Shell.qml is now line 72.

The change in common/IconTile.qml remains the same.

The changes in launcher/LauncherList.qml are now on lines 31 and 35.

That seems to be it.

---

### Post by bonzini on 2012-03-25
A new set of QML files today; here are the line numbers:

Shell.qml: line 75
common/IconTile.qml: lines 71,72
launcher/LauncherList.qml: lines 31,35

Seems to continue to work fine.

---

### Post by queenofbabes on 2012-04-03
It works, thanks!
(Really now, I can't imagine why the big, fat icons are the default size...)

---

### Post by Roasted on 2012-04-03
Not to intrude, but is this behavior expected to remain even on final release? Or are the icons supposed to gain resizable functionality?

---

### Post by bonzini on 2012-04-15
New files again today (yesterday?), line numbers are now

Shell.qml: line 89
common/IconTile.qml: 71,72
launcher/LauncherList.qml: 31,35

(editorial comment)

I don't get why the default size is so big, either.  On a vertical bar on a short / wide screen they are so big that one is soon into scrolling the launcher.  They are much bigger than icons in any application I can think of, too - imagine if the icons in Firefox or LibreOffice were that big!

On the topic of being able to change them in the Settings menu, I recall reading somewhere (a bug, maybe) that this ability is not coming before 12.10, which is what prompted me to figure out this work-around.

I'm still looking for a solution to make the workspace selector icon fit better, and also a solution to make the icons in the dash smaller and take up less room...

---

### Post by momist on 2012-04-30
Thank you SO much for this.  My major hate for Unity was focussed on me not being able to change the stupidly ginormous icons on my 19" (non-widescreen) monitor.    :)

There are other things . . .  but another time.

> **bonzini said:**
> 

Now you need to check, and possibly change, one last thing.  In the same "launcher" directory, examine line 250 in the file "LauncherItem.qml".  If it looks like

```
width: 32
```



This was set to 32 already in my plain vanilla precise pangolin, and now appears on line 259 for those who wish to check.

Now I can patiently await development of the nVidia driver for my nine year old FX5200 silent video card.  I have no need for super fast graphics, but so wish I could run the Unity 3D version so that things "just work".

Thanks for you help!

---

### Post by wolfie25 on 2012-05-02
Thanks a lot guys. It works. Have changed the icons to a smaller and still usable size. 
I am using 12.10 LTS (the beta version but with updates). According to the help in documentation, one can change launcher icon size via System Settings/Appearance. I tried it but there was no icon size sliding bar in my Appearance setting. Anyone using 12.10 and find this feature absent?

---

### Post by edgue on 2012-05-04
> **wolfie25 said:**
> Thanks a lot guys. It works. Have changed the icons to a smaller and still usable size. 
I am using 12.10 LTS (the beta version but with updates). According to the help in documentation, one can change launcher icon size via System Settings/Appearance. I tried it but there was no icon size sliding bar in my Appearance setting. Anyone using 12.10 and find this feature absent?

I guess you mean 12.04.

But I fully agree to your posting - Google points out that there should be a slider on the "appearance settings" panel to control the launcher icon size.

I just installed 12.04 in a virtual machine - and this slider is not there.
I tried the old fashioned way: installing compiz config manager; and there is an entry in the ubuntu desktop plugin page for that icon size ... but this setting doesnt have any effect.

So, how the f**##!! does one reduce the insane icon size of the launcher? And what on earth where the unity folks thinking here?

---

### Post by vasa1 on 2012-05-04
@bonzini, your instructions worked perfectly. Thanks for figuring all this out for us at the cost of a weekend!

---

### Post by wolfie25 on 2012-05-04
> **edgue said:**
> I guess you mean 12.04.

But I fully agree to your posting - Google points out that there should be a slider on the "appearance settings" panel to control the launcher icon size.

I just installed 12.04 in a virtual machine - and this slider is not there.
I tried the old fashioned way: installing compiz config manager; and there is an entry in the ubuntu desktop plugin page for that icon size ... but this setting doesnt have any effect.

So, how the f**##!! does one reduce the insane icon size of the launcher? And what on earth where the unity folks thinking here?

Sorry, I am using 12.04. 

It was quite fun changing the various .qml s to get the size of the icons reduced. I am relearning vi and bash. The exercise gave me a chance to use vi and bash. 

Perhaps the documentation and help guys should change their page to reflect the real situation. 

I am really glad to find the solution. Isn't that what Linux is about.

---

### Post by edgue on 2012-05-05
> **wolfie25 said:**
> Sorry, I am using 12.04. 


I wasnt precise either. I am struggling with icon size using unity 3d; not 2d. And so far I wouldnt find any qml files in the unity directory ...

---

### Post by vasa1 on 2012-05-08
There were some updates today and it's back to the big icons for Unity 2D. Let's see if the instructions, allowing for new line numbers, will still work.

---

### Post by mailc on 2012-05-09
After the latest update yesterday the icons are again large.

So I found the .qml files but some also had .bak files.
So I made copies of the files to the Desktop, made my changes there, and moved the original .qml files and their backup files to a folder and replaced them with the files on my Desktop.
The original .qml files were safely in a folder which i kept just in case,  but that was not needed.

I suppose that some of you  may be laughing   but I am not comfortable using the superuser option to make such changes (the ony 2 commands used were : ' gksudo gedit '  and ' sudo mv ' ) .   gedit did not show lines but that was actually better for me since i used the 'Find' option.

Hope that this will be of use for some people not that experienced (like myself).

---

### Post by vasa1 on 2012-05-09
> **mailc said:**
> ...   gedit did not show lines ...
Hi!
If you open gedit and then click on **Edit**, **Preferences**, you can see *Display line numbers* at the top in the **View** tab.

---

### Post by pieterio on 2012-07-23
this has GOT TO BE the coolest thing to do for me to have my ultimate desktop environment: i am running Cubuntu which is a Ubuntu 12.04 100% but with cinnamon desktop AND launcher (unity-2d obviously) even gnome if you want to, or full Unity 3d ..available here: [www.cubuntu.fr](www.cubuntu.fr) (it's French to begin with but easily changes into english because built on full ubuntu 12.04 basis)
 
it's absolutely amazing....for the quick buttons i have the launcher, now in a fair size thanks to you :) whereas for admin stuff and programs i rarely use i have the cinnamon menu structure instead of the dash which i didn't like that much.

GOD I LOVE THIS WHOLE LINUX COMMUNITY!!!

thanks ever so much

Pieter

---

### Post by sumithar on 2012-07-26
Thanks!
In 11.10 you could go into Compiz Experimental settings and change but while the option exists it doesn't seem to "take".
This worked.

---

### Post by Mycen on 2012-09-26
Thanks for this! Since my eyesight isn't that bad I found the huge bulky icons a tad on the offensive side. Thanks to you, I now have a sexy slim launcher again. 

As for my 2 cents, gedit (out of the box) does show line numbers in the status bar, but the search option is of course far more convenient, since the line numbers change all the time. (as seen in the forum discussion above)

Cheers!

---

### Post by yashoda on 2012-09-29
fantastic stuff!!

this worked perfectly!

THANK YOU!

---

### Post by patrick2310 on 2012-09-30
Thank you bonzini. Your message did 2 things. Fixed the icons **AND **gave me a taste of using terminal and sudo.  And don't worry, I'll be careful with the latter.
Thanks again.

---

### Post by morone on 2012-12-01
Thank you for posting this information - it worked for me and made the display of the desktop look so much better than the standard stock size icons.

---

### Post by Joe2832 on 2013-04-12
Thanks for posting. It changed the icons to a small size.  I'd like to make them size 39 seen in Unity 3d.  Anyone know offhand what the corresponding numbers in 2d would be?

---

### Post by scbingham on 2013-04-22
Absolutely brilliant!  What a fabulous improvement.

Thank you very much.

---

### Post by nisargshah on 2013-08-21
Great tweak! Thanks man, really helpful!!!

---

### Post by allCuExpMa on 2014-01-16
Brillant, thanks for the very helpfull tweak. It worked like a charm.

---

