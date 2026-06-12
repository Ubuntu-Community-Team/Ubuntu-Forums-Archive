---
title: "Howto recover the big pointer in unity?"
date: 2012-08-26
forum: Desktop Environments
---

### Post by claracc on 2012-08-26
I had a big cursor (icon size 48) in 10.04, when I upgraded to 12.04, this big cursor remains big only incertain apps, i.e. firefox, but when I move cursor in the desktop or open nautilus it appears very very small.

How can I recover my big cursor for all the system and apps?, only I want to change the cursor size to a bigger one

---

### Post by Frogs Hair on 2012-08-26
This has been the case for me on every version of Ubuntu I have used starting with 9.10 . This is why stopped trying install custom cursors.The cursor changes on hover regardless of what internet browser is used. Advanced Settings allows changing the style and not the size.

---

### Post by stinkeye on 2012-08-26
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11929215&postcount=17") to use **galternatives**
to add and select your mouse theme and then use gnome-tweak-tool to also select it.
Install galternatives...
```
sudo apt-get install galternatives
```

[COLOR="Red"]*****NOTE*****[/COLOR]
Your cursor theme must have a **cursor.theme** file.
If not create one in the same format as other themes.
eg look at the cursor.theme file in **/usr/share/icons/DMZ-White**

---

### Post by claracc on 2012-08-26
Thanks for answering.

I have my cursor theme whiteglass in /usr/share/icons, I don't want to change the cursor's theme but only its size. In fact I have a cursor size of 48 in a .Xresources file and with dconf-editor I can see that the cursor theme whiteglass and size 48 are the correct.

But the problem is when I hover the pointer in the launcher or desktop or top panel it changes its size to a very small one (very little arrow), it occurs generally in the top part of the windows. However in firefox window the cursor size is the correct, the big one which I had in lucid.

I have tried the two methods suggested in this link: [http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](http://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size) but it doesn't work

---

### Post by stinkeye on 2012-08-26
As far as I know, the only way to increase the cursor size and have
it work properly is to install a theme like big-cursor and use the 
method posted earlier.

---

### Post by claracc on 2012-08-27
The problem is really weird.

While I see the correct size cursor(big one) in certain apps: firefox or libreoffice; in desktop, launcher, panel and almost every other window I see a very small arrow as cursor ( when in certain parts of these windows cursor changes to a hand its size is always big, the desired one). 

I have taken a screenshot of my desktop to demonstrate how small is the cursor but although I see the cursor small in the display, in the screenshot taken it appears as the big one I want¿¿???. 

I am really puzzled.

---

### Post by vasa1 on 2012-08-27
You should read the link given by Stinkeye carefully. There are two different types of mouse cursor behavior. You need to set both.

---

### Post by stinkeye on 2012-08-27
> **claracc said:**
> The problem is really weird.

While I see the correct size cursor(big one) in certain apps: firefox or libreoffice; in desktop, launcher, panel and almost every other window I see a very small arrow as cursor ( when in certain parts of these windows cursor changes to a hand its size is always big, the desired one). 

I have taken a screenshot of my desktop to demonstrate how small is the cursor but although I see the cursor small in the display, in the screenshot taken it appears as the big one I want¿¿???. 

I am really puzzled.

It's a long standing bug that I've yet to see a solution for
except installing a customized large cursor theme.
The dconf setting for cursor-size doesn't apply across the whole system.

I downloaded  a pretty basic large cursor theme and when installed as described earlier, works.

---

### Post by claracc on 2012-08-27
Thankyou very much. At the end I got it. The procedure you gave works.

At least I understood which the problem was.

I downloaded and installed, as you addressed, the Large cursor theme and now, yes, it works. I don't have my old pretty and big whiteglass pointer but I got a big basic one and no the small little arrow.

Now I will look for more cursor themes (bigger ones) to try.

Is there a bug in launchpad to fill about this problem?

Best regards

---

### Post by som21 on 2013-01-25
> **claracc said:**
> 
Is there a bug in launchpad to fill about this problem?

Best regards

the bug is already running; for sometimes. :popcorn:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184)

---

### Post by stinkeye on 2013-01-25
In 12.10 this method works without installing any additional themes.
Two changes to make.

Set the cursor size in dconf.
Terminal...
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR="Magenta"]xx[/COLOR]
```
Where [COLOR="magenta"]xx[/COLOR] is your cursor size.
Default is 24.
Use 16, 32, 48, or 64.

and

Edit ~/.Xresources
```
gedit ~/.Xresources
```
and add or edit the line
```
Xcursor.size:[COLOR="magenta"]xx[/COLOR]
```
using the same value you used for dconf.

Need to reboot.

---

### Post by zombifier25 on 2013-01-25
> **som21 said:**
> the bug is already running; for sometimes. :popcorn:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184)

Interesting. But it doesn't just happen in Compiz, it's in every WM I have tried, so it's probably a bug in the X server, not Compiz.
Also, that darn bug is 5 years old now, so it's not gonna be fixed anytime soon.

Linux based OSs are the only OSes that has this kind of ridiculous bug. The X server is really ancient, so let's hope Wayland will be better.

---

### Post by zika on 2013-02-14
> **stinkeye said:**
> In 12.10 this method works without installing any additional themes.
Two changes to make.

Set the cursor size in dconf.
Terminal...
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR="Magenta"]xx[/COLOR]
```
Where [COLOR="magenta"]xx[/COLOR] is your cursor size.
Default is 24.
Use 16, 32, 48, or 64.

and

Edit ~/.Xresources
```
gedit ~/.Xresources
```
and add or edit the line
```
Xcursor.size:[COLOR="magenta"]xx[/COLOR]
```
using the same value you used for dconf.

Need to reboot.Yes that works... Thank You...
No need to reboot. Just restart X (reatart DM, whatever You use) or use xrdb... Reboot is for other OS...

---

### Post by claracc on 2013-02-15
> **stinkeye said:**
> In 12.10 this method works without installing any additional themes.
Two changes to make.

Set the cursor size in dconf.
Terminal...
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR="Magenta"]xx[/COLOR]
```
Where [COLOR="magenta"]xx[/COLOR] is your cursor size.
Default is 24.
Use 16, 32, 48, or 64.

and

Edit ~/.Xresources
```
gedit ~/.Xresources
```
and add or edit the line
```
Xcursor.size:[COLOR="magenta"]xx[/COLOR]
```
using the same value you used for dconf.

Need to reboot.
 Does it work in a fully updated 12.04 system using metacity and gnome fallback desktop?.

Thanks in advance

---

### Post by stinkeye on 2013-02-15
Don't have 12.04 to test.
Replaced with 13.04.

Works in my 12.10 install in both the **ubuntu** and the **gnome classic(no effects)** sessions.

---

### Post by claracc on 2013-02-15
Thankyou

I will try the workaround in my 12.04 system and will post the results. I suppose I can always go back to my current cursor reinstalling the big cursor theme, isn't it?

---

### Post by claracc on 2013-02-15
No, this workaround doesn't work in 12.04 with gnome fallback session.

If I want a big cursor I have to install a large cursor theme.

---

### Post by cmcanulty on 2013-03-20
I also have this problem in 12.04 classic and would also like a black cursor which is what I have set in advanced settings and dconf editor but it changes on some apps to white and small. This is a real irritating bug that used to be easy to fix in gnome 2

---

### Post by ManamiVixen on 2013-03-20
The cursor bug is a bug in X.Org and has been there since the X.Org version present in Ubuntu 9.04. It will not be fixed anytime soon. There is a work around involving manually taking your preferred cursor theme and making it default by renaming the "default" folder in the /usr/share/icon folder to something else like "default-old", then taking you cursor theme and rename it "default". Reboot and it should work.

---

### Post by stinkeye on 2013-03-20
> **cmcanulty said:**
> I also have this problem in 12.04 classic and would also like a black cursor which is what I have set in advanced settings and dconf editor but it changes on some apps to white and small. This is a real irritating bug that used to be easy to fix in gnome 2

Use galternatives to also change to the same theme under x-cursor-theme.
or
run the command
```
sudo update-alternatives --config x-cursor-theme
```

---

### Post by cmcanulty on 2013-03-20
I installed the galternatives but issue still exists. I get a large black pointer in firefox but other stuff is still small and white I have also used Ubuntu tweak, and advanced settings, and dconf but none fix this problem. A few releases ago this got broken and nothing seems to fix it. I am running 12.04 classic.

---

### Post by stinkeye on 2013-03-20
Ubuntu-tweak and other tweak tools just change the dconf setting(gsettings)
Changing the cursor from DMZ-White to DMZ-Black should work by changing the gsettings and alternatives value.

The size of the cursor is a different issue.
If the size is inconsistent change the cursor-size back to default (24).
```
gsettings **reset** org.gnome.desktop.interface cursor-size
```

Using the ~/.Xresources file to make the size consistent doesn't work in 12.04.

---

### Post by cmcanulty on 2013-03-20
The issue is to get a large pointer consistently as I have bad eyesight, this should be a very basic tweak

---

### Post by stinkeye on 2013-03-20
> **cmcanulty said:**
> The issue is to get a large pointer consistently as I have bad eyesight, this should be a very basic tweak
It should be but it's not.

To have a larger cursor you need to download a theme which is made larger and add it to the alternatives list and then change to that theme using dconf and alternatives.

This thread shows how to install a theme that highlights the mouse.
[http://ubuntuforums.org/showthread.php?t=2124489&p=12552311&viewfull=1#post12552311]("http://ubuntuforums.org/showthread.php?t=2124489&p=12552311&viewfull=1#post12552311")

---

### Post by cmcanulty on 2013-03-20
I have a larger cursor but it isn't consistent. In firefox it is large and blavk on the desktop it is small and white

---

### Post by stinkeye on 2013-03-20
> **cmcanulty said:**
> I have a larger cursor but it isn't consistent. In firefox it is large and blavk on the desktop it is small and white
As I said before you cant change the size consistently using the default themes.

You need to have downloaded a theme like the one I attached earlier in this thread (post #8) that has been created as a larger size.
If you have downloaded a different large cursor theme, post a link to the cursor theme download or attach a .tar.gz of your theme and I'll show you how to add it to the alternatives list.

---

### Post by cmcanulty on 2013-03-20
ok I have looked at gnome-look and there are hundreds but they don't say the size. I prefer 48 black just like I have in firefox now. Is there a way to locate the one I am using in firefox. I looked in the icons but there are hundreds of files there

---

### Post by stinkeye on 2013-03-20
> **cmcanulty said:**
> ok I have looked at gnome-look and there are hundreds but they don't say the size. I prefer 48 black just like I have in firefox now. Is there a way to locate the one I am using in firefox. I looked in the icons but there are hundreds of files there
You can install big-cursor from the repos.
Normally it's black but changes to white (still big though) when hovering over links.
See pics.
If your happy with that let me know as it still requires you to make a **cursor.theme** file.

---

### Post by stinkeye on 2013-03-20
Ok try this one.
Install comixcursors...
```
sudo apt-get install comixcursors-righthanded-opaque
```

The comixcursors themes do not contain cursor.theme files.
In order to add to alternatives the theme needs a cursor.theme file.
You need to create a cursor.theme file for the ComixCursors-Opaque-Black-Large theme.
```
gksudo gedit /usr/share/icons/ComixCursors-Opaque-Black-Large/cursor.theme
```

...and copy and paste into the created cursor.theme file
```
[Icon Theme]
Inherits=ComixCursors-Opaque-Black-Large
```
Save and close.


Using the terminal, add the theme to alternatives...
```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/ComixCursors-Opaque-Black-Large/cursor.theme 20
```


Using the terminal, select the theme in dconf and alternatives...
```
CURSOR=ComixCursors-Opaque-Black-Large
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```
Log out/in


If you want to change back to the default cursor (DMZ-White)...
```
CURSOR=DMZ-White
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme
```
Log out/in

As you can see I've used a variable ($CURSOR) for the name of the theme so if you want to set it back to black
use **CURSOR=DMZ-Black** instead of CURSOR=DMZ-White in the first command.

---

### Post by cmcanulty on 2013-03-21
OK I installed the big-cursor from synaptic which I had tried a while ago without any luck. Also I tried the command sequence above which just produces errors see below

```
cmcanulty@darcytech:~$ sudo apt-get install comixcursors-righthanded-opaque
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
comixcursors-righthanded-opaque is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cmcanulty@darcytech:~$ [Icon Theme]
[Icon: command not found
cmcanulty@darcytech:~$ Inherits=ComixCursors-Opaque-Black-Large
cmcanulty@darcytech:~$ sudo mv ~/cursor.theme /usr/share/icons/ComixCursors-Opaque-Black-Large/
mv: cannot stat `/home/cmcanulty/cursor.theme': No such file or directory
cmcanulty@darcytech:~$ sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/ComixCursors-Opaque-Black-Large/cursor.theme 20
update-alternatives: error: alternative path /usr/share/icons/ComixCursors-Opaque-Black-Large/cursor.theme doesn't exist.
cmcanulty@darcytech:~$ 

```

---

### Post by stinkeye on 2013-03-21
> **stinkeye said:**
> Create a cursor.theme file.
Save as **cursor.theme** to your home folder.
```
[COLOR="#FF0000"][Icon Theme]
Inherits=ComixCursors-Opaque-Black-Large[/COLOR]
```



[COLOR="#FF0000"]This[/COLOR] is meant to be copied and pasted into gedit and saved as **cursor.theme** to your home folder

---

### Post by cmcanulty on 2013-03-21
OKJ I have that file in my home folder - see screenshot but still get following error

```
cmcanulty@darcytech:~$ sudo mv ~/cursor.theme /usr/share/icons/ComixCursors-Opaque-Black-Large/
[sudo] password for cmcanulty: 
mv: cannot stat `/home/cmcanulty/cursor.theme': No such file or directory
cmcanulty@darcytech:~$ 

```

---

### Post by stinkeye on 2013-03-21
> **cmcanulty said:**
> OKJ I have that file in my home folder - see screenshot but still get following error

```
cmcanulty@darcytech:~$ sudo mv ~/cursor.theme /usr/share/icons/ComixCursors-Opaque-Black-Large/
[sudo] password for cmcanulty: 
mv: cannot stat `/home/cmcanulty/cursor.theme': No such file or directory
cmcanulty@darcytech:~$ 

```

If its there it will open with gedit
```
gedit /home/cmcanulty/cursor.theme
```
If it doesn't you saved wrong place or name.

[COLOR="#FF0000"]EDIT[/COLOR]: I've changed it so you create the cursor.theme file
directly in the theme folder instead of home and then moving.

---

### Post by cmcanulty on 2013-03-21
It opens with gedit. OK I got it installed but unfortunately it is too small. Accessibiity should be a basic function of Ubuntu. Thanks for all your help. Not solved.

---

### Post by stinkeye on 2013-03-21
> **cmcanulty said:**
> It opens with gedit. OK I got it installed but unfortunately it is too small. Accessibiity should be a basic function of Ubuntu. Thanks for all your help. Not solved.
Yep ok.

---

### Post by stinkeye on 2013-03-25
> **cmcanulty said:**
> It opens with gedit. OK I got it installed but unfortunately it is too small. Accessibiity should be a basic function of Ubuntu. Thanks for all your help. Not solved.

Try this.
I took the installed DMZ-Black theme and removed the 24 and 32 pixel layers so it uses 48 and
created a DMZ-Black-Large theme.

Download the attachment to your ~/Downloads folder.
Right click on ~/Downloads/DMZ-Black-Large.tar.gz > Extract here.
Move theme to /usr/share/icons...
```
sudo mv Downloads/DMZ-Black-Large /usr/share/icons
```

Add to alternatives, change to theme in dconf and alternatives and change size to 48 pixels (4 separate commands)....
```
CURSOR=DMZ-Black-Large

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings set org.gnome.desktop.interface cursor-size 48
```
Log out/in

To set back to default cursor and size...
```
CURSOR=DMZ-White

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings reset org.gnome.desktop.interface cursor-size
```
Log out/in

---

### Post by cmcanulty on 2013-03-25
Wow this is difficult I have a bunch of cursors I copied tio usr/share/icons but still get this error. I don't know where to get the file "DMZ-Black-Large". I don't see it in synaptic or with a google search. I also have the large mouse cursor folder and contents, see last 2 screenshots. I am totally frustrated with this. Should be easy
```
cmcanulty@darcytech:~$ CURSOR=DMZ-Black-Large
cmcanulty@darcytech:~$ sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20
[sudo] password for cmcanulty: 
update-alternatives: error: alternative path /usr/share/icons/DMZ-Black-Large/cursor.theme doesn't exist.
cmcanulty@darcytech:~$
```
 I guess none of the cursors I downloaded work Below is a screenshot of the directory and the cursors
[ATTACH=CONFIG]240529[/ATTACH][ATTACH=CONFIG]240530[/ATTACH]

---

### Post by stinkeye on 2013-03-25
Bit confused here.
The **DMZ-Black-Large** cursor theme is one I made from the  DMZ-Black theme.

I attached it to my last post and you need to download it to your Downloads folder and extract it
before any of the commands will work.
The very first command in my previous post, moves the extracted DMZ-Black-Large theme to /usr/share/icons

---

### Post by cmcanulty on 2013-03-25
Oh, sorry IO missed that and now it seems fixed. This has been bugging me for 2 years! Thanks very much.

---

### Post by stinkeye on 2013-03-25
> **cmcanulty said:**
> Oh, sorry IO missed that and now it seems fixed. This has been bugging me for 2 years! Thanks very much.
No problem, I needed this for my failing eyesight as well, and I also prefer the default back cursor.

---

### Post by cmcanulty on 2013-03-29
Well I guess it isn't as fixed as I thought. On the 10 laptops I run at the library (all identical HP g72t) it worked on 7 . On 3 it worked for the guest user but not the admin librarian account. I did the commands in the librarian account as the guest account is a limited user. Any ideas on this?

---

### Post by cmcanulty on 2013-03-29
Apparently I spoke too soon. On 10 identical HP laptops at the library, all HP g72t it worked on 7. On 3 it changed to big and black on the limited user but not the admin account. On one it is big but white. And they are set correctly in dconf editor.I hope someone can help on this.

---

### Post by spundot on 2013-06-02
@stiinkeye, thanks for the instructions and creating the DMZ-Black-Large package. :D

This fixed the situation for me on 12.10 - trying to use Ubuntu on a TV without squinting for the cursor.

Everything else I tried only made the cursor large some of the time.

---

### Post by rtimai on 2013-06-30
I just now discovered that one of the recent Ubuntu updates (30 June 2013) -- probably to X.org -- appears to have fixed the cursor bug in which the large cursor took effect only within certain application windows. I don't know how the large cursor is set in dconf-editor, but in Unity Tweak (you have to install this optional tool) there is a Cursor module where you can select "Use large cursor." And this setting now works! --at least in this login session. My fingers are crossed. Will report back here if the large cursor is not persistent.

Follow-up: I cold booted, and the large cursor did not appear on the desktop or in the Files (Nautilus) window. However, the large cursor appeared when I started Chromium (which I believe is GTK-based.) But it now persists in the desktop and Nautilus (which I believe are non-GTK applications.)

I think this is just one of the reasons that Canonical is working to replace X Windows with the new Mir display system, to avoid all the regression errors caused by all the obsolete code in X.

---

### Post by stinkeye on 2013-06-30
> **rtimai said:**
> I just now discovered that one of the recent Ubuntu updates (30 June 2013) -- probably to X.org -- appears to have fixed the cursor bug in which the large cursor took effect only within certain application windows. I don't know how the large cursor is set in dconf-editor, but in Unity Tweak (you have to install this optional tool) there is a Cursor module where you can select "Use large cursor." And this setting now works! --at least in this login session. My fingers are crossed. Will report back here if the large cursor is not persistent.

Follow-up: I cold booted, and the large cursor did not appear on the desktop or in the Files (Nautilus) window. However, the large cursor appeared when I started Chromium (which I believe is GTK-based.) But it now persists in the desktop and Nautilus (which I believe are non-GTK applications.)

I think this is just one of the reasons that Canonical is working to replace X Windows with the new Mir display system, to avoid all the regression errors caused by all the obsolete code in X.
What Ubuntu release are you using?

Using unity-tweak-tool to "use large cursors" doesn't work for me in 13.04.
Still changes size and theme inconsistently.

---

### Post by rtimai on 2013-06-30
stinkeye, I'm running Ubuntu 13.04 Unity. 

Do you, by any chance, have "Icons on desktop" in Unity Tweak turned OFF? I seem to recall this setting (a.k.a. "allow Nautilus to control the desktop") had to be ON to avoid several other annoying symptoms. If you already have it turn ON, then I'm afraid I don't know what's going on here. I can't find any setting in dconf-editor that seems to refer to the desktop cursor either. A lot has been sealed in a black box since Unity (maybe for our own safety.) Good luck with your cursor.

---

### Post by rtimai on 2013-06-30
I am running Ubuntu 13.04 Unity.
 
I don't know if this directly affects the cursor, but do you have "Icons on desktop" turned ON? This setting (a.k.a. "allow Nautilus to control the desktop") has an effect on several other annoying symptoms. If you already have it turned ON, I'm afraid I don't have anything else to suggest. If you're already using the workaround described earlier, then -- maybe -- the change in default folder structure may be affecting this fix. Good luck on your big cursor effort.

---

### Post by stinkeye on 2013-07-01
Nautilus is managing the desktop.
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **gsettings get org.gnome.desktop.background show-desktop-icons**
true
```

So using unity-tweak-tool, if you set the cursor theme to dmz-white by hitting the "restore defaults" button 
and then select "use large cursors", is the size consistent? Isn't here.

The "use large cursors" appears to just change this dconf setting (default is 24)....
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **gsettings get org.gnome.desktop.interface cursor-size**
48
```

In 12.04 & 13.04 the only way for me to get a consistently large cursor is to use a cursor theme that only has one large size.
eg 
[**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046&p=12572902&viewfull=1#post12572902"), where I removed the 24 and 32 pixel layers from the DMZ-Black theme so it has to use 48.

---

### Post by rtimai on 2013-07-01
Thanks stinkeye, you're right, the cursor-size setting is in dconf, not in gconf. Also, yes, I used Unity Tweak as you described above to set the large cursor. I don't know why these settings are not affecting your desktop cursor size. (I'm not celebrating yet. It remains to be seen whether this behavior persists over the next few days.)

---

### Post by rtimai on 2013-07-01
glen (stinkeye),
You reported:

glen@Raring:~$ gsettings get org.gnome.desktop.interface cursor-size
48

If this is a gconf setting, this key no longer exists in my gconf configuration -- it doesn't appear in gconf-editor. An Interface key does appear in dconf-editor -- but oddly enough it is NOT changed to 48 but remains the default 24 (with "Use large cursor" selected in Unity Tweak.) 

My double-size cursor remains persistent between cold boots. Notably, however, the cursor size starts out small (24) when initially logging in, and the large cursor appears to be activated only after starting the Chromium browser or Gnome-Search. I think the GTK-based rendering of these applications are what triggers the large cursor. In previous versions of Ubuntu, however, the large cursor reverted back to the small size when leaving the GTK-based application. This time however, however awkwardly activated, the large cursor remains persistent. I don't know which Ubuntu Unity update fixed the cursor-size setting, or if it was even intentional. But I seem to recall a recent update to X.org, the underlying display system, and I suspect this is what caused the new behavior. I suspect that a regression error in the future could easily cause the bug to resurface.

---

### Post by cmcanulty on 2013-07-01
this needs an easy fix it works on some machines, others it shows as 48 black in dconf but is still small worked fine in gnome 2

---

### Post by stinkeye on 2013-07-01
> **rtimai said:**
> glen (stinkeye),
You reported:

glen@Raring:~$ gsettings get org.gnome.desktop.interface cursor-size
48

If this is a gconf setting, this key no longer exists in my gconf configuration -- it doesn't appear in gconf-editor. An Interface key does appear in dconf-editor -- but oddly enough it is NOT changed to 48 but remains the default 24 (with "Use large cursor" selected in Unity Tweak.) 

My double-size cursor remains persistent between cold boots. Notably, however, the cursor size starts out small (24) when initially logging in, and the large cursor appears to be activated only after starting the Chromium browser or Gnome-Search. I think the GTK-based rendering of these applications are what triggers the large cursor. In previous versions of Ubuntu, however, the large cursor reverted back to the small size when leaving the GTK-based application. This time however, however awkwardly activated, the large cursor remains persistent. I don't know which Ubuntu Unity update fixed the cursor-size setting, or if it was even intentional. But I seem to recall a recent update to X.org, the underlying display system, and I suspect this is what caused the new behavior. I suspect that a regression error in the future could easily cause the bug to resurface.

Hi rtimai,
gsettings is a commandline interface to dconf.
One of gsettings commands allows you  to  **monitor** individual keys or keys from a schema.
I did this when using unity-tweak to "restore defaults" and "use large cursors" and it showed the dconf changes in terminal as they happened.
Still inconsistent here.
unity-tweak-tool version 0.0.5

If it works for you...just run with it. :)

---

### Post by xxbartosxx on 2013-07-02
> **stinkeye said:**
> Try this.
I took the installed DMZ-Black theme and removed the 24 and 32 pixel layers so it uses 48 and
created a DMZ-Black-Large theme.

Download the attachment to your ~/Downloads folder.
Right click on ~/Downloads/DMZ-Black-Large.tar.gz > Extract here.
Move theme to /usr/share/icons...
```
sudo mv Downloads/DMZ-Black-Large /usr/share/icons
```

Add to alternatives, change to theme in dconf and alternatives and change size to 48 pixels (4 separate commands)....
```
CURSOR=DMZ-Black-Large

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings set org.gnome.desktop.interface cursor-size 48
```
Log out/in

To set back to default cursor and size...
```
CURSOR=DMZ-White

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings reset org.gnome.desktop.interface cursor-size
```
Log out/in

How would I make one for the redglass theme all sizes out exept 48?

Grts

---

### Post by stinkeye on 2013-07-02
> **xxbartosxx said:**
> How would I make one for the redglass theme all sizes out exept 48?

Grts
Hi xxbartosxx,
It's quicker for me to actually  gimp the theme than explain how to do it,
but if you want a howto, let me know and I'll post when I have time.


Download the attachment, extract the **redglass-Large** folder and move to /usr/share/icons...

Then run these 4 terminal commands...
```
CURSOR=redglass-Large

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings set org.gnome.desktop.interface cursor-size 48
```
Log out/in.


To set back to DMZ-White default size(24)....
```
CURSOR=DMZ-White

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings reset org.gnome.desktop.interface cursor-size
```

---

### Post by xxbartosxx on 2013-07-02
Works like a charm but you don't need to do the gsettings stuff as I am on xubuntu. A HowTo would be rather handy if I wonne edit other themes.

Grtz & Thx

---

### Post by stinkeye on 2013-07-03
_**[SIZE=3]Using gimp to remove pixel layers.[/SIZE]**_
Copy your cursor theme from /usr/share/icons or a downloaded theme to your Desktop.
I have not used gimp much and it only allows me to save in the correct format with an extension so I can't replace 
the original images directly when saving in gimp.
So firstly I add a .xmc extension to all the image files in the theme's cursors folder with **pyrenamer**.
```
sudo apt-get install pyrenamer
```
Open pyrenamer at the cursors folder and set up as in pic. Hit Preview then Rename.
Renaming allows me to overwrite the original file when saving in gimp.
[ATTACH=CONFIG]244343[/ATTACH]

Now in the themes cursor folder you may see a lot of files with broken link symbols.
You only need ctrl select the files that are not linked and then open in gimp.
Arrange files by file_type and select only non linked images.
The broken links will be fixed when the extensions are removed.
[ATTACH=CONFIG]244344[/ATTACH]


Now it's just a production line in gimp.
Click and hold on the small arrow on the left of the images bar until you stop at the first image.
[ATTACH=CONFIG]244348[/ATTACH]
On the right is the layers tab and shows the different pixel layers.
Click on the top most layer (usually 48px) in the right pane then hold the keyboard down Arrow to move to the bottom.
The reason for this is it remembers the last layer selection when deleting.
Hit the delete button repeatedly until you are left with only 48 pixel layers.  
Be aware that some of the animated images have multiple 48 pixel layers you don't want to delete.

Click on the next image in the imported image bar and repeat....repeat .....

Then you need to save each edited image.
[ATTACH=CONFIG]244346[/ATTACH]

File > overwrite...for each image.

Once you have overwritten all files select
File > close all 
You will be warned about unsaved changes.
The files are already overwritten...so just choose discard changes and close gimp.
 

Then you need to remove the .xmc extensions in the theme's cursors folder.
Open with pyrenamer and set up as in pic below. Hit Preview then Rename.
[ATTACH=CONFIG]244347[/ATTACH]

Edit the _cursor.theme_ file to something to reflect the change.
A **cursor.theme** file is needed to register the theme with update-alternatives.
If a downloaded theme doesn't have this file, create it.
```
[Icon Theme]
Inherits=**DMZ-White-Large**
```

and also edit the _index.theme_ to...
```
[Icon Theme]
Name=DMZ-White-Large
Comment=White large cursor theme
```

Lastly rename the theme folder to the new name shown in the cursor.theme file. 
In this example... **[COLOR="#FF0000"]DMZ-White-Large[/COLOR]**, and move to **/usr/share/icons**

Register the theme with update-alternatives and  select the theme as shown previously... 
```
CURSOR=[COLOR="#FF0000"]DMZ-White-Large[/COLOR]

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings set org.gnome.desktop.interface cursor-size 48
```
The above commands will work with any theme placed in **/usr/share/icons** that has a cursor.theme file. 
Just change the first command to the name of your cursor theme.
ie 
**CURSOR=***[COLOR="#FF0000"]modified_theme_name[/COLOR]*
The last command, "**gsettings set org.gnome.desktop.interface cursor-size 48**" command isn't really needed because it can't use anything else but 48 pixels.

---

### Post by rtimai on 2013-07-04
I stated that I'd report here if the large cursor reverted. It DID REVERT, for no apparent reason, Dconf settings remain the same. The 'working' circle animation and 'select' hand are large -- in some windows only -- and the arrow cursor is back to the small 24px size again. On a laptop with 1366x768 resolution, the small screen cursor is difficult to locate. Such a disappointment. Thanks for our comments.

FOLLOW-UP WORKAROUND!

Stinkeye provided an excellent procedural for modifying complete cursor theme sets. My situation, however, is somewhat specific, not requiring a cursor overhaul, and I thought I'd add my simple workaround here for others who have trouble locating the small arrow-pointer on the screen. Now, I've tried ALL the dconfig and update-alternatives solutions posted here, but the arrow-pointer has not been affected -- while all the other cursors are double in size when selecting the "large cursors" option.

So, I used Stinkeye's excellent instructions for modifying the arrow-pointer file (left_ptr) ONLY, to contain only one layer with a size 32 image with the hotspot at axes 1x1. I've uploaded this file as a public file to my UbuntuOne account storage folder. 

So, here's a really simple fix for what I wanted: Replace the /usr/share/icons/DMZ-White/cursors/left_ptr file with the file located at:

[http://ubuntuone.com/3tc2EYtSsSp6hUxWaQjC4t](http://ubuntuone.com/3tc2EYtSsSp6hUxWaQjC4t)

The easiest way for those unfamiliar with the command line to perform a file replacement is to open Terminal and enter:

gksudo nautilus
      or
gksudo nemo
   (if you prefer Nemo for its ability to display the left pane in Tree View)

Navigate to and locate /usr/share/icons/DMZ-White/cursors/left_ptr

FIRST RENAME the left_ptr file to left_ptr~ to preserve the original copy!

Then COPY the modified file to the DMZ-White/cursors folder

Logging in/out should activate the new arrow-pointer immediately at the LightDM login screen. ALL of my cursor options in Unity-Tweak-Tool are set at defaults. Hope this helps somebody.

And THANKS to Stinkeye for the GIMP instructions. Information on editing XMC file layers is not easy to find.

---

### Post by stinkeye on 2013-07-18
Can someone check this for me in an up to date 13.04 install.
It appears 13.04 now observes the **~/.Xresources** file for cursor size like previously.

eg 
When using one of the default DMZ themes,
I only need to set the size with gsettings...
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR="#EE82EE"]48[/COLOR]
```

and

edit ~/.Xresources with the same size change
```
gedit ~/.Xresources
```
add or edit the line
```
Xcursor.size:[COLOR="#EE82EE"]48[/COLOR]
```
log out/in.

---

### Post by rtimai on 2013-07-18
Stinkeye,

I am confirming, Unity is now parsing the ~/.Xresources file, and it DOES fix the cursor size problem. 

As you'd expect, this takes effect AFTER logging in. The LightDM/Plymouth screen starts out with the tiny 24-pixel pointer (in a 1366x768 resolution laptop screen,) then it enlarges when the desktop loads. But there are still issues with the icon theme. I tried switching to DMZ-Black, and the arrow pointer remains white, while the Wait (spinner,) Select (hand,) and resize arrows are black. 

Okay... I see now, the icon theme needs to be re-set in update-alternatives also. I used Galternatives and confirmed that the theme was still set to DMZ-White, and when I changed it to match Dconf (gsettings) the arrow pointer size updated to 48-point. 

I'm not sure if the Plymouth screen will ever show the large pointer, but it's trivial as far as I'm concerned. Thanks for the heads-up about this change. (And I have the workaround 48-pixel DMZ-Black theme to fall back on if this gets "regressioned" out.) HOW did you notice it?

---

### Post by rtimai on 2013-07-18
Oh, just a moment. I thought I'd tried an entry in ~/.Xresources before, but i think I was confusing it with an .Xdefaults file in the same location, that didn't work. This might just be a new discovery for Ubuntu Unity.

---

### Post by stinkeye on 2013-07-18
> **rtimai said:**
> Stinkeye,

I am confirming, Unity is now parsing the ~/.Xresources file, and it DOES fix the cursor size problem. 

As you'd expect, this takes effect AFTER logging in. The LightDM/Plymouth screen starts out with the tiny 24-pixel pointer (in a 1366x768 resolution laptop screen,) then it enlarges when the desktop loads. But there are still issues with the icon theme. I tried switching to DMZ-Black, and the arrow pointer remains white, while the Wait (spinner,) Select (hand,) and resize arrows are black. 

Okay... I see now, the icon theme needs to be re-set in update-alternatives also. I used Galternatives and confirmed that the theme was still set to DMZ-White, and when I changed it to match Dconf (gsettings) the arrow pointer size updated to 48-point. 

I'm not sure if the Plymouth screen will ever show the large pointer, but it's trivial as far as I'm concerned. Thanks for the heads-up about this change. (And I have the workaround 48-pixel DMZ-Black theme to fall back on if this gets "regressioned" out.) HOW did you notice it?
Thanks rtimai,
Changing the dconf value and editing the ~/.Xresources file worked in 12.10 but didn't work in 13.04 before.

I noticed it just recently started working when I switched back to the default DMZ-white theme and size of 24.
When I logged back in the desktop displayed a large cursor because I still had an old **~/.Xresources** file defining **Xcursor.size:48 **

So for now, anyone with inconsistent cursor size, just use the dconf setting
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR="#EE82EE"]xx[/COLOR]
```
and
```
gedit ~/.Xresources
```
adding
```
Xcursor.size:[COLOR="#EE82EE"]xx[/COLOR]
```

Where [COLOR="#EE82EE"]xx[/COLOR] is your chosen cursor size.
[COLOR="#EE82EE"]24[/COLOR] is the default size 
[COLOR="#EE82EE"]32[/COLOR] is a nice size for a PC
[COLOR="#EE82EE"]48[/COLOR] is a good size for a TV

If it breaks again you can use one of the 4 attached themes I made
[LIST=1]
[*]DMZ-White-Medium ...32px
[*]DMZ-White-Large ....48px
[*]DMZ-Black-Medium ...32px
[*]DMZ-Black-Large ....48px
[/LIST]


and install as described in previous posts.

---

### Post by rtimai on 2013-07-18
Stinkeye, thank you for the DMZ icon theme sets, they're definitely keepers, masterpieces of consistency. Oh yeah, you did a redglass-Large as well.

---

### Post by zika on 2013-07-18
> **stinkeye said:**
> Thanks rtimai,
Changing the dconf value and editing the ~/.Xresources file worked in 12.10 but didn't work in 13.04 before.

I noticed it just recently started working when I switched back to the default DMZ-white theme and size of 24.
When I logged back in the desktop displayed a large cursor because I still had an old **~/.Xresources** file defining **Xcursor.size:48 **

So for now, anyone with inconsistent cursor size, just use the dconf setting
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR=#EE82EE]xx[/COLOR]
```
and
```
gedit ~/.Xresources
```
adding
```
Xcursor.size:[COLOR=#EE82EE]xx[/COLOR]
```

Where [COLOR=#EE82EE]xx[/COLOR] is your chosen cursor size.
[COLOR=#EE82EE]24[/COLOR] is the default size 
[COLOR=#EE82EE]32[/COLOR] is a nice size for a PC
[COLOR=#EE82EE]48[/COLOR] is a good size for a TV

If it breaks again you can use one of the 4 attached themes I made
[LIST=1]
[*]DMZ-White-Medium ...32px
[*]DMZ-White-Large ....48px
[*]DMZ-Black-Medium ...32px
[*]DMZ-Black-Large ....48px
[/LIST]


and install as described in previous posts.Or use dconf-editor...

---

### Post by stinkeye on 2013-07-18
> **zika said:**
> Or use dconf-editor...
Yep obviously, for half the solution.

---

### Post by zika on 2013-07-18
> **stinkeye said:**
> Yep obviously, for half the solution.
Limited by the fact that I'm using 13.10+Ricotz and many other PPAs I can just answer: dconf-editor change is immediately visible at my desktop... I did have before .Xresources file but I retired it months ago...

---

### Post by stinkeye on 2013-07-18
> **zika said:**
> Limited by the fact that I'm using 13.10+Ricotz and many other PPAs I can just answer: dconf-editor change is immediately visible at my desktop... I did have before .Xresources file but I retired it months ago...
Why not include that info in your original comment?

---

### Post by zika on 2013-07-18
> **stinkeye said:**
> Why not include that info in your original comment?
I stand corrected and I will try to correct my future behavior appropriately...
I've forgot that I'm not in U+1 part of this huge place... Even do not remember how I got into this thread...
I've noticed that only after I wrote my post... Count that to my old age and...

---

### Post by rtimai on 2014-04-19
Stinkeye,

Upgrading to Ubuntu 14.04 Trusty Tahr has broken the .Xresources file setting. The cursor size (medium or large) set on the desktop in that file reverts to the default 24 when starting Gedit or Chromium, and then remains small on the desktop. So, your fix (including the modified simple fix replacing only the left_ptr file with your replacement version) continues to be useful.

Supposedly Canonical is developing an X.org display server replacement called XMir/Mir for Ubuntu, while everyone else is eventually transitioning to Wayland. Either way, I hope that moving off X.org -- which is supposedly bloated with legacy code that makes it difficult for developers to avoid bugs -- will help solve the cursor issues that plague Linux users -- especially of those with failing eyesight. Thank you for your patience and persistence with your good work.
 :popcorn:

---

### Post by rtimai on 2014-04-19
Stinkeye's redglass-Large.tar.gz is also available in message #54 of this thread. I don't know how to link it in this message, but this collection may come in handy on future Ubuntu upgrades!

---

### Post by grumblebum2 on 2014-04-19
> **rtimai said:**
> Stinkeye,

Upgrading to Ubuntu 14.04 Trusty Tahr has broken the .Xresources file setting. The cursor size (medium or large) set on the desktop in that file reverts to the default 24 when starting Gedit or Chromium, and then remains small on the desktop. So, your fix (including the modified simple fix replacing only the left_ptr file with your replacement version) continues to be useful.

Supposedly Canonical is developing an X.org display server replacement called XMir/Mir for Ubuntu, while everyone else is eventually transitioning to Wayland. Either way, I hope that moving off X.org -- which is supposedly bloated with legacy code that makes it difficult for developers to avoid bugs -- will help solve the cursor issues that plague Linux users -- especially of those with failing eyesight. Thank you for your patience and persistence with your good work.
 :popcorn:
Testing in 14.04 seems to show that the **~/.Xresources** file is still used but the dconf setting **org.gnome.desktop.interface cursor-size** is now overridden by **com.canonical.Unity.Interface cursor-scale-factor** when logging in to unity.

eg I can set a consistent cursor size of 32 pixels with the terminal command...
```
echo "Xcursor.size:32" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
```
Log out then back in.

For a larger 48 pixel size...
```
echo "Xcursor.size:48" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
```

 
The dconf setting **com.canonical.Unity.Interface cursor-scale-factor** has a range of 1.00 to 3.00 and alters the **org.gnome.desktop.interface cursor-size** setting.
eg
```
[COLOR="#008000"]@Trusty:~$[/COLOR] gsettings reset org.gnome.desktop.interface cursor-size
[COLOR="#008000"]@Trusty:~$[/COLOR] gsettings get org.gnome.desktop.interface cursor-size
[COLOR="#FF0000"]24[/COLOR]
[COLOR="#008000"]@Trusty:~$[/COLOR] gsettings set com.canonical.Unity.Interface cursor-scale-factor **1.35**
[COLOR="#008000"]@Trusty:~$[/COLOR] gsettings get org.gnome.desktop.interface cursor-size
[COLOR="#FF0000"]32[/COLOR]
```

---

### Post by rtimai on 2014-04-20
@grumblebum2: Thanks very much for your clever testing and new key information. Your instructions are a keeper! All my cursors are now large. The Tweak Unity tool as well needs to be updated with this new setting. As the discoverer you should notify the developer:  [https://launchpad.net/unity-tweak-tool](https://launchpad.net/unity-tweak-tool)

---

### Post by Djzn.BR on 2015-01-03
I can confirm this is working for me, on Utopic Unicorn...
Previously to this tweak, I could not resize the pointer consistently across the system, for the life of me, in any previous release versions.

```
echo "Xcursor.size:32" > ~/.Xresources && gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
```

---

### Post by rtimai on 2015-01-04
> Djzn.BR;13200222]I can confirm this is working for me, on Utopic Unicorn...

@Djzn.BR: Thanks for your confirmation. I use Xcursor.size 48 and cursor-scale-factor 2 on my HP dv6 laptop, and these settings were preserved in an upgrade from 14.04 Trusty to 14.10 Utopic. 

Macular degeneration makes it hard for me to spot a 24-small cursor on a screen -- and I hope Ubuntu continues to support Accessibility features, and that this tweak eventually finds its way into the Universal Access settings in the Ubuntu System Settings. Still, with the mass migration to mobile devices, perhaps we shouldn't hold our breaths.

---

### Post by Djzn.BR on 2015-01-04
> Macular degeneration makes it hard for me to spot a 24-small cursor on a screen -- and I hope Ubuntu continues to support Accessibility features, and that this tweak eventually finds its way into the Universal Access settings in the Ubuntu System Settings. Still, with the mass migration to mobile devices, perhaps we shouldn't hold our breaths.

I understand you. I also have a low to mid degree myopia on my eyes, plus astigmatism on top of it. 
The default 24 cursor kind of makes sense on the laptop. However, it is really tiny on a 23 inch panel.
Like you said I think this tweak was working on previous versions too, but I only got to know this on this release.
Actually I haven't been on this forum for a while and my last post was about abandoning Ubuntu, when Unity landed.
However I recognize that Unity has come a long way and I am sure more improvements will be made.
The incorporation of LIM is a sign that things are evolving to a very mature level and accessibility.
Cheers.

---

### Post by ben2talk on 2015-01-22
> **som21 said:**
> the bug is already running; for sometimes. :popcorn:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/86184)

I never understood the real problem - perhaps now I do, or at least - I fixed it for myself.

After installing Chameleon cursors, I found my true love. Not quite the normal pointy arrow, but very lovely nonetheless and you can select between White, Black (anthracite which is a dark grey still visible on Black), Pearl and... a nice blue which stands out on just about any background... but not a bright blue, more a dusky blue.

My advice is to get these cursors... They're in my synaptic, I'm sure not an advanced theme (do main search for icon, browse and select anything you fancy there, then type 'chameleon' in quick search...

Check them out with your Themes selector, then open a terminal and do 
```
sudo update-alternatives --config x-cursor-theme
```

Choose the theme to be applied as your 'ROOT' cursor theme.

If you use 'Theme' to select another cursor, the 'ROOT' cursor theme will still show when mousing over Chromium browser...

---

### Post by rtimai on 2015-01-22
@ben2talk: Thanks for a good contribution! As a test, I used the GUI methods, installed it from Software Center, where searching for "chameleon," it appears as "modern but not gaudy X11 mouse theme," and selected Anthracite-Large in the DConf settings with "gksu galternatives." I agree, it's a very well-designed theme set, beautiful.

As Ubuntu transitions to the Mir display system, while every other non-Ubuntu distro moves to Wayland, we might expect the .Xresources/com.canonical.Unity.interface workaround to eventually fail. The chameleon-cursor-theme, however might survive the transition, and I think this could be an important contribution to the cursor size issue. Thanks again!

---

### Post by CantankRus on 2015-01-22
If you like to test different cursors and sizes I wrote this script to easily change between different installed cursors.
Cursors must be installed to **/usr/share/icons** and have a **cursor.theme** file.

It will also change the size when using Trusty 14.04.
Changing of size will only work with cursor themes that are made with the different pixel layers.

Script needs to be run in terminal.
**_change_cursor-trusty_**
```
#!/bin/bash

#set -x

####################################################################
##                                                                ##
##     Script to change cursors. Only lists themes installed to   ##
##     /usr/share/icons.                                          ##
##     Theme must have a cursor.theme file                        ##
##                                                                ##
####################################################################

####################################################################
##                                                                ##
## To change the cursor theme, the script will                    ##
##  1) Change dconf setting                                       ##
##  2) Register the theme with update-alternatives                ##
##  3} Select the theme in update-alternatives                    ##
##                                                                ##
## To change the cursor size the script will                      ##
##  1) Change dconf setting                                       ##
##  2) Edit the ~/.Xresources file or create if                   ##
##         it doesn't exist                                       ##
##                                                                ##
##      ....................................                      ##
##      :   Tested in Ubuntu Trusty 14.04  :                      ##
##      :..................................:                      ##
####################################################################

## Adapted for Trusty as it uses a new setting for cursor size
## gsettings set com.canonical.Unity.Interface cursor-scale-factor

#color codes
startcolor=\\033[36m
endcolor=\\033[0m

CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
THEME=$(gsettings get org.gnome.desktop.interface cursor-theme)
touch ~/.Xresources

echo -e "\n*** This script tested in Ubuntu Trusty 14.04 ***\n"
echo -e "\n$startcolor Your current cursor theme is $endcolor$THEME$startcolor of size $endcolor$CURRENTSIZE$startcolor pixels$endcolor\n"
#ask to restore to default
echo -e "$startcolor To choose a new theme just press the$endcolor \"Enter\"$startcolor key or\n type$endcolor \"d\"$startcolor and press$endcolor \"Enter\"$startcolor to reset theme to default$endcolor:"
read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
		echo
	else
		echo -e "\n$startcolor You have chosen to reset the cursor theme to default ...Continue?$endcolor(Y/n):"
			read Ans
				if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
					then
						echo -e "\n$startcolor Using update-alternatives requires Authentication of Admin privileges...$endcolor"
							gsettings reset org.gnome.desktop.interface cursor-theme && sudo update-alternatives --set x-cursor-theme /usr/share/icons/DMZ-White/cursor.theme
							sed -i "/Xcursor.size/c\\" ~/.Xresources
							gsettings reset com.canonical.Unity.Interface cursor-scale-factor	#new setting in Trusty overrides Saucy setting below
							gsettings reset org.gnome.desktop.interface cursor-size		#for Saucy
							#sed -i '/CursorThemeName/c\sGtk\/CursorThemeName=DMZ-White' ~/.config/lxsession/Lubuntu/desktop.conf  #Lubuntu
							sleep 1
							DSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
							THEME=$(gsettings get org.gnome.desktop.interface cursor-theme)
						echo -e "$startcolor--------------------------------------------------------$endcolor"
						echo -e "\n$startcolor Your cursor theme has been reset to $endcolor$THEME$startcolor of size $endcolor$DSIZE$startcolor pixels$endcolor";	
							read -n 1 -p "Press any key to exit this script..." 
						exit
					else
							read -n 1 -p "Press any key to exit this script..."
						exit
			 	fi
fi

## create installed cursor list text file
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort > ~/.cursorlist.txt
#ack-grep "Inherits=" /usr/share/icons | grep "cursor.theme" | cut -f 2 -d '=' | sort > ~/.cursorlist.txt
#ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt


 
## show a numbered list of cursors to choose from
echo -e "\n---$startcolor Cursor themes in /usr/share/icons$endcolor ---"
cat -b ~/.cursorlist.txt 
 
echo -e "$startcolor Enter your new theme selection number:$endcolor"
read CHOICE


## match the theme selection number to the cursor name
#CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p')
CURSOR=$(sed -n "$CHOICE"'p' < ~/.cursorlist.txt)
	echo -e "\n$startcolor You have selected $endcolor$CURSOR\n$startcolor Continue?$endcolor(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
		echo -e "\n$startcolor Using update-alternatives requires Authentication of Admin privileges...$endcolor"
	else
		echo -e "\nYou chose not to continue...\n"
		echo -e "\n$startcolor Your current cursor theme is $endcolor$THEME"
		read -n 1 -p "Press any key to exit this script..."
	exit
fi


## Change to selected  cursor
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme 20
sleep 1
sudo update-alternatives --set x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme


## Set size of cursor in unity. Trusty uses a dconf cursor-scale-factor setting which sets the cursor-size
CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
#CURRENTSCALE=$(gsettings get com.canonical.Unity.Interface cursor-scale-factor)
echo -e "\n$startcolor Your current cursor size is $endcolor$CURRENTSIZE \n$startcolor Would you like to change the size?$endcolor(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
		echo  
	else
		echo -e "$startcolor--------------------------------------------------------$endcolor"
		echo -e "\nYou chose not to continue..." 

		## writes to or creates a ~/.Xresources file to reflect curent cursor size. Need to do this when choosing not to change size and ~/.Xresources doesn't exist
		echo -e "\n$startcolor You have enabled the $endcolor$CURSOR$startcolor cursor theme with size unchanged of $endcolor$CURRENTSIZE$startcolor \nYou need to log out to complete the change$endcolor";
			if grep "Xcursor.size:" ~/.Xresources > /dev/null; then
				#echo "Xcursor.size line exists"
				sed -i "/Xcursor.size/c\Xcursor.size:${CURRENTSIZE}" ~/.Xresources
			else
				#echo "Xcursor.size line does not exist"
				echo "Xcursor.size:${CURRENTSIZE}" >> ~/.Xresources
			fi
		read -n 1 -p "Press any key to exit this script..."
 	exit
fi

## Choose size
echo -e "$startcolor Choose your new cursor-size from 24, 32, 48, or 64  Default=24$endcolor"
	read SIZE

## Confirm choice
echo -e "\n$startcolor You have selected a cursor size of$endcolor $SIZE\n$startcolor Continue?$endcolor(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
    	echo 
	else
		echo -e "\nYou chose not to continue..."
	  	echo -e "\n$startcolor You have enabled the $endcolor$CURSOR$startcolor cursor theme with size unchanged of $endcolor$CURRENTSIZE$startcolor \nYou need to log out to complete the change$endcolor";
		echo
	 read -n 1 -p "Press any key to exit this script..."
exit
fi

## Edits dconf to reflect chosen size for Saucy 
gsettings set org.gnome.desktop.interface cursor-size $SIZE

## match size to cursor-scale-factor for Trusty
case "$SIZE" in

# 24=cursor-scale-factor 1
24)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1
;;

# 32=cursor-scale-factor 1.35
32)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
;;

# 48=cursor-scale-factor 2
48)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
;;

# 64=cursor-scale-factor 2.65
64)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2.65
;;

# input error
*)
echo -e  "\n$startcolor*** OOps wrong size ....Try again ***$endcolor"
;;
esac


## Creates a ~/.Xresources file or edits existing to reflect chosen size
if grep "Xcursor.size:" ~/.Xresources > /dev/null 
	then
		#echo "Xcursor.size line exists"
		sed -i "/Xcursor.size/c\Xcursor.size:${SIZE}" ~/.Xresources
	else
		#echo "Xcursor.size line does not exist"
		echo "Xcursor.size:${SIZE}" >> ~/.Xresources
fi
echo -e "$startcolor--------------------------------------------------------$endcolor"
echo -e "\n$startcolor You have enabled the $endcolor$CURSOR$startcolor cursor theme of size $endcolor$SIZE$startcolor pixels $endcolor";

echo -e "$startcolor You need to log out to complete cursor change\n$endcolor";
read -n 1 -p "Press any key to exit this script..."  
```

---

### Post by rtimai on 2015-01-23
Thanks for the script, CantankRus. I'm no programmer, but I'm guessing you're quite experienced with BASH. If I get a chance to test it, I'll report here. I do think it should work in 14.10 Utopic as well, as the settings are stored identically. Thanks again for an impressive contribution. I'm no one in the Ubuntu community, but you deserve acknowledgment from somebody.

---

### Post by CantankRus on 2015-01-23
> **rtimai said:**
> Thanks for the script, CantankRus. I'm no programmer, but I'm guessing you're quite experienced with BASH. If I get a chance to test it, I'll report here. I do think it should work in 14.10 Utopic as well, as the settings are stored identically. Thanks again for an impressive contribution. I'm no one in the Ubuntu community, but you deserve acknowledgment from somebody.
Nah, I'm your self taught home variety scripter that manages to kludge something together by looking at other scripts but thanks for the kind words.

---

### Post by tp-groen on 2015-05-22
The following worked for me on my ultra-hd screen, where visibility of the default pointer is a real problem:

1. Use dconf-editor for black cursor, size 48
2. Create .Xresorces file containing the line Xcursor.size:48

I had bad experience restarting Unity as suggested somewhere in one of the threads, so I waited for the next reboot.

---

