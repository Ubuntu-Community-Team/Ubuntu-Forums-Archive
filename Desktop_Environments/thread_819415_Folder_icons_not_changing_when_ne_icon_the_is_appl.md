---
title: "Folder icons not changing when ne icon the is applied"
date: 2008-06-05
forum: Desktop Environments
---

### Post by pmlxuser on 2008-06-05
I have downloaded a few Icon themes, butwhen i apply theme in my theme manager "Basically the > System> Preferences > Appearance >  Theme" All the other system icons change but the folder icons don't Change specifically when i Apply the following Icons Themes
1.AquaFusion
2.Kearon's Icons

I have downloaded also Gion & Lila Icon Themes and these causes no problem.
Any assistance will be appriciated.

---

### Post by Darkshade on 2008-06-12
Up?:rolleyes:

---

### Post by ethos101 on 2008-07-06
bump :D

---

### Post by jw5801 on 2008-07-06
Try restarting X (log out then log back in) after applying the theme. If folder icons still haven't changed, I would be looking at whoever made the icon package, not at Ubuntu/Nautilus.

---

### Post by sayakb on 2008-07-06
Hardy is it? Open your home folder. Press Ctrl+H and open the **.icons** folder. Open the theme folder.
That is, goto ~/.icons/themename/48x48/places and replace the **folder.png** and **gnome-fs-directory.png** with the icon you want. Also change this icon of different sizes. If the theme already has a custom icon present with the above filenames, then, you might try something else ;)

---

### Post by ethos101 on 2008-07-06
Apparently on further research there is already a bug report with Hardy and the folder icons.  From what I understand it has something to do with a new naming convention.  Why you would CHANGE naming conventions mid-stream defeats the purpose of having a naming convention, doesn't it?  Oh well.  Hopefully they fix it soon.

---

### Post by jw5801 on 2008-07-07
Never mind. That statement was wrong :P

---

### Post by gdp77 on 2008-07-08
Similar problem here. I use compiz with emerald theme manager and I cannot change the **ICON THEME** from system--->preferences--->appearance. I can choose the "default" icons mist, human, etc. , but no change will happen if I choose a downloaded theme like snow apple, noia, stylish etc. (some icons do change, but folder icons remain the shame)

Anyone has any idea what to do?

---

### Post by jw5801 on 2008-07-08
> **gdp77 said:**
> Similar problem here. I use compiz with emerald theme manager and I cannot change the **ICON THEME** from system--->preferences--->appearance. I can choose the "default" icons mist, human, etc. , but no change will happen if I choose a downloaded theme like snow apple, noia, stylish etc. (some icons do change, but folder icons remain the shame)

Anyone has any idea what to do?

Yes, in fact LinuxIsInnovation already answered the question with a post in this thread, just 3 posts above where you're now reading. Alternatively, you can read it [here](http://ubuntuforums.org/showthread.php?p=5329765#post5329765).

---

### Post by ethos101 on 2008-07-08
> **LinuxIsInnovation said:**
> Hardy is it? Open your home folder. Press Ctrl+H and open the **.icons** folder. Open the theme folder.
That is, goto ~/.icons/themename/48x48/places and replace the **folder.png** and **gnome-fs-directory.png** with the icon you want. Also change this icon of different sizes. If the theme already has a custom icon present with the above filenames, then, you might try something else ;)

The problem is that they're .SVG filetypes.  So yes one does exist for "gnome-fs-directory.SVG" but it deosn't show up as folder icons.  There is none for "folder.SVG" or ".PNG" for that matter.

[SOLVED]
I simply copied the "gnome-fs-directory.SVG" to filename "folder.SVG" in the existing folder which was a bit different from where you mentioned (~/.icons/IconThemeName/scalable/filesystems/) and it works now.

Thanks for the input L-I-I and everyone!  :D

---

### Post by taurusx5 on 2008-08-05
ethos101, can you pleae explain to me how you managed to get the folder icons to show? In my ~/.icons/IconThemeName/scalable/filesystems, I see the folder icons as being .png, not .svg. The theme I'm trying to get to show is 'Snow Apple'. 

Please, let me know. I got 8.04. Thanks!

---

### Post by jw5801 on 2008-08-05
> **taurusx5 said:**
> ethos101, can you pleae explain to me how you managed to get the folder icons to show? In my ~/.icons/IconThemeName/scalable/filesystems, I see the folder icons as being .png, not .svg. The theme I'm trying to get to show is 'Snow Apple'. 

Please, let me know. I got 8.04. Thanks!

The fix will stay the same! You just need to change the name of the file, regardless of the extension.

Although having .pngs as scalables is incredibly bad practice on the part of the theme creator. Scalable Vector Graphics are infinitely scalable and will look the same when made much bigger, Portable Network Graphics, however, will blur and look terrible when scaled.

---

### Post by ethos101 on 2008-08-06
I just renamed the file from gnome-fs-directory.* to just plain folder.*

---

### Post by taurusx5 on 2008-08-06
> **jw5801 said:**
> The fix will stay the same! You just need to change the name of the file, regardless of the extension.

Although having .pngs as scalables is incredibly bad practice on the part of the theme creator. Scalable Vector Graphics are infinitely scalable and will look the same when made much bigger, Portable Network Graphics, however, will blur and look terrible when scaled.

jw5801, tell me if I'm doing this right since I'm having touble with your instructions. I go to: ~/.icons/IconThemeName//48x48/filesystems and locate gnome-fs-directory.png to which I renamed to folder.png. But, nothing happens. The folders in my computer stay the same and don't change at all. I've also tried to rename gnome-fs-directory-accept.png to folder.png also but again, nothing happens. 

What must I do now? By the way, Im trying to install the 'snow apple' icon theme. 

.

---

### Post by jw5801 on 2008-08-07
Try doing the same to the other other size of the file, so rather than the 48x48 folder, try the others in that directory and apply the same fix.

---

### Post by taurusx5 on 2008-08-09
> **jw5801 said:**
> Try doing the same to the other other size of the file, so rather than the 48x48 folder, try the others in that directory and apply the same fix.

jw5801, I renamed gnome-fs-directory.png to just folder.png for all file sizes in the directory and nothing happens. The folders all stay the same regardless. Any other ideas at this point?

---

### Post by ethos101 on 2008-08-09
You kinda have to figure out what the name of the folder icon the skin is expecting and see if you can rename the folder icon to it.  Or see if it's looking in the wrong place and move it there.

I'm too new to be able to guide you more specifically than that but thats generally what I did to fix mine and what I told you worked for me.

---

### Post by sudeeraj on 2008-08-10
Try this,

1 ) Open a Text editor



2 ) Goto 
[INDENT]~/.icons/**IconThemeName**[/INDENT]



3 )Drag and drop the "**index.theme**" onto the text editor



4 )On the third or forth line, you will find,

[INDENT]"**Inherits=gnome**" or "**Inherits=core**" [/INDENT]

[INDENT]Change it to "**Inherits=none**"[/INDENT]




5 )save the file and exit the Text editor



6 ) Depending on the presence of folders goto[INDENT] 
~/.icons/**IconThemeName**/48x48/filesystems[/INDENT]
or
[INDENT]
~/.icons/**IconThemeName**/scalable/filesystems[/INDENT]


7 ) Take a copy of "**gnome-fs-directory.[COLOR="Blue"]AnyExtention[/COLOR]**" and paste it in the same folder. (Now you will have have "**gnome-fs-directory (copy).[COLOR="Blue"]AnyExtention[/COLOR]**")



8 ) Rename the "**gnome-fs-directory (copy).[COLOR="Blue"]AnyExtention[/COLOR]**" to "**folder.[COLOR="Blue"]AnyExtention[/COLOR]**"



9 ) Open "System--->Preferences--->Appearance" and change the icon set to another icon set.



10 ) Change back again to the icon set you modified.

Done.



Ps..(I found this later)
Goto [COLOR="Blue"]/usr/share/icons/Human/scalable[/COLOR]
and according to the icon file names there, rename corresponding the icon filenames in your installed icons folder, in order for all icons to work.! (It's very hard to rename all, you can rename just only some of the icons that you want)

---

### Post by taurusx5 on 2008-08-12
> **sudeeraj said:**
> Try this,

1 ) Open a Text editor



2 ) Goto 
[INDENT]~/.icons/**IconThemeName**[/INDENT]



3 )Drag and drop the "**index.theme**" onto the text editor



4 )On the third or forth line, you will find,

[INDENT]"**Inherits=gnome**" or "**Inherits=core**" [/INDENT]

[INDENT]Change it to "**Inherits=none**"[/INDENT]




5 )save the file and exit the Text editor



6 ) Goto [INDENT]
~/.icons/**IconThemeName**/48x48/filesystems[/INDENT]



7 ) Take a copy of "**gnome-fs-directory.[COLOR="Blue"]AnyExtention[/COLOR]**" and paste it in the same folder. (Now you will have have "**gnome-fs-directory (copy).[COLOR="Blue"]AnyExtention[/COLOR]**")



8 ) Rename the "**gnome-fs-directory (copy).[COLOR="Blue"]AnyExtention[/COLOR]**" to "**folder.[COLOR="Blue"]AnyExtention[/COLOR]**"



9 ) Open "System--->Preferences--->Appearance" and change the icon set to another icon set.



10 ) Change back again to the icon set you modified.

Done.


sudeeraj, thanks for the reply. I tried your instructions and I was able to change all the icons on my computer EXCEPT for the folder icons. The folder icons are default icons that are grey in color. I really don't understand this. Can you offer any further instructions about this? I'd really appreciate it. 

.

.

---

### Post by taurusx5 on 2008-08-12
sudeeraj, forget my prior post. Your instructions did the trick! I forgot to do something per your instructions, and for a while there I was stuck. But, I got my icon theme working big time !!! Thanks a million, man!!!!!!! You're a life saver!

.

---

### Post by woaibbhemm on 2008-08-12
hello~:KS
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by sudeeraj on 2008-08-13
> **taurusx5 said:**
> sudeeraj, forget my prior post. Your instructions did the trick! I forgot to do something per your instructions, and for a while there I was stuck. But, I got my icon theme working big time !!! Thanks a million, man!!!!!!! You're a life saver!

.

Thank you taurusx5 :)

---

### Post by ben2talk on 2008-08-17
> **gdp77 said:**
> Similar problem here. I use compiz with emerald theme manager and I cannot change the **ICON THEME** from system--->preferences--->appearance. I can choose the "default" icons mist, human, etc. , but no change will happen if I choose a downloaded theme like snow apple, noia, stylish etc. (some icons do change, but folder icons remain the shame)

Anyone has any idea what to do?


I am working on it now with 'Glass Icons' theme, which has ONLY one folder with scalable icons. It goes well with 'H20-gtk2-' glassy buttons, but although many icons are replaced the folders aren't. It's not simply a matter of renaming them. Some work and some don't, and it's 2am so I'll maybe play with it another day.

---

### Post by sudeeraj on 2008-08-18
> **ben2talk said:**
> I am working on it now with 'Glass Icons' theme, which has ONLY one folder with scalable icons. It goes well with 'H20-gtk2-' glassy buttons, but although many icons are replaced the folders aren't. It's not simply a matter of renaming them. Some work and some don't, and it's 2am so I'll maybe play with it another day.

Didn't you try setting **Inherits=none**? 
[URL="http://ubuntuforums.org/showpost.php?p=5561586&postcount=17"]
http://ubuntuforums.org/showpost.php?p=5561586&postcount=17[/URL]

I think it should work fine.

---

### Post by EnGorDiaz on 2008-08-18
i made my own icon there have a look at this i call it newXgen
the cairo dock works with it too its about 27mb worth of icons ;)

---

### Post by triplek on 2008-08-23
I try everything. On Ubuntu 8.04 gnome svg icons not work. :(

/Edit
On my debian's gnome dont work too. On debian's xfce working. I dont understand. <_<

---

### Post by qtrung1305 on 2008-11-27
Thank you sudeeraj. It works fine. :)

---

### Post by locodog on 2010-06-14
Well, it kinda solves problem, but now only my folder icons are replaced, desktop remains the same like it is on Gnome theme. And also when i try other themes it doesn't work, so i must do this for every theme I want to use... it's kinda stupid.

---

### Post by marticc on 2010-06-16
Hi, I' ve just updated my ubuntu and got the Ubuntu 10.04.

I am quite happy with the default theme, but I don't like the default icon for folders (home, documents,downloads...) is there a way of changing all the folder icons (and use the folder icon of other theme), without changing the whole theme.

Thanks.

Sorry for my poor English.

---

