---
title: "Nautilus Default Settings in 15.04"
date: 2015-04-27
forum: Desktop Environments
---

### Post by mark bower on 2015-04-27
Installing 15.04 and gnome-session-flashback.

Where/how do I set the Nautilus default settings in 15.05?  The menu bar (file edit view go bookmarks) is no longer present when Nautilus is opened; the defaults were entered via the menu bar in 12.04.  I want to always display directories as List.  

I can set my Home directory to List using the List Icon, but the setting is not retained after leaving and returning to /Home.  There is a post suggesting "file>preferences", but I do not see how to get to it in 15.05 Gnome Desktop.  The icons in the upper right corner when Nautilus is opened are Search, List, Grid(icon display), View Options, Location Options.

---

### Post by grahammechanical on 2015-04-27
Ubuntu 15.04 defaults to showing menus in the window's title bar.  Mouse over the window's title bar or go to System Settings>Appearance>Behaviour tab and change it to In the menu bar.

Anyway, Nautilus in 15.04 should be showing three square boxes at the top right - Search; View items as a list; and View items as a grid of icons. These functions are certainly present in the Unity UI and any change done there should carry over into Gnome Flashback.

Regards.

---

### Post by mark bower on 2015-04-27
"In the Menu Bar" was already set as a function of the install.  I am thinking your display differs from mine; for me Nautilus always displays "5" icon buttons(I listed them in my initial post and called them "icons"), not 3 in the upper right hand corner.  Again, I have the Gnome desktop.  And again, yes the selections for list or icon view work, but list view does not remain, nor remain as global.  

A significant change has been made for Nautilus going from version in 12.04 to 15.04, or somewhere in between.  In 12.04 the Nautilus changes were made in a menu bar shown when Nautilus was opened.  The the only icon in the upper right was a Search button.

So, more help or more explanation is needed on how to set my directories to permanently display in List mode, ie, how to set the default to List?

---

### Post by mark bower on 2015-04-27
o.k., the following command line looks to do the trick, I tested it twice.  But what a nuisance how Nautilus was changed for use with Gnome Classic!  I am not marking thread as solved as I am guessing there may be more negative issues to resolve. 

```
gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'

```
The link which uncovered the above CLI command:

[https://wiki.archlinux.org/index.php/GNOME_Files#Change_default_item_view](https://wiki.archlinux.org/index.php/GNOME_Files#Change_default_item_view)

---

### Post by dino99 on 2015-04-28
dconf (from dconf-editor) is the place now where settings are hold

---

### Post by mc4man on 2015-04-28
it's a flaw in gnome flashback sessions as they use the gnome session version of nautilus where preferences is in the app menu. However in either of the flashback sessions there is no app menu so no preferences.
Maybe it could be fixed, maybe not as not too many dev's spend any time on flashback.

If desired there is an undefined accel in nautilus for preferences so it can be user defined, example in screen, set to ctrl+p
(requires a nautilus restart after setting

---

### Post by mark bower on 2015-04-28
@mc4man

Your ... 14:10.jpg(the 1st one) shows **exactly** the pop-up I am/was after - full control of Files(Nautilus).  How do you install "gtk-accel" or whatever enables getting the pop-up in 15.04?  I will try it if the steps are not too complicated?

However, the fix I used per post #4 seems to give me the functionality that I need.  By any chance do you know where the configuration files are located that were altered by the gsettings command used per post #4?  I have not been clever enuf to locate.

---

### Post by mc4man on 2015-04-28
> **mark bower said:**
> @mc4man

Your ... 14:10.jpg(the 1st one) shows **exactly** the pop-up I am/was after - full control of Files(Nautilus).  How do you install "gtk-accel" or whatever enables getting the pop-up in 15.04?  I will try it if the steps are not too complicated?

However, the fix I used per post #4 seems to give me the functionality that I need.  By any chance do you know where the configuration files are located that were altered by the gsettings command used per post #4?  I have not been clever enuf to locate.
The file & location are  shown in the screenshots, as in  > home folder > .config/nautilus or go 
```
gedit ~/.config/nautilus/accels
```
(- user set accels must not have ; at line start, again shown clearly  in screenshot.

dconf (gsettings)  setting are stored in a binary file, nothing   there to read, ect.  ( .config/dconf/user

---

### Post by mark bower on 2015-04-28
o.k.  I went to ~/.config/nautilus/accels and the file is empty.  But it is not clear to me what to do next.  Is the line '  gtk_accel_path ..."<Primary>p")  ' supposed to be entered in the accels file.

The following line made no sense for me, especially "user set accels must not have"?
(- user set accels must not have ; at line start, again shown clearly in screenshot.

---

### Post by mc4man on 2015-04-28
> **mark bower said:**
> o.k.  I went to ~/.config/nautilus/accels and the file is empty.  But it is not clear to me what to do next.  Is the line '  gtk_accel_path ..."<Primary>p")  ' supposed to be entered in the accels file.

The following line made no sense for me, especially "user set accels must not have"?
(- user set accels must not have ; at line start, again shown clearly in screenshot.

Hmm, should be there with lines in it.  (if it was then the bit about ; would be obvious. My previous gedit screenshot shows that. All autoset accels are commented with a ; user set ones can't have that.

Did you start with Ubuntu then install gnome-flashback or did you start with Ubuntu-Gnome?

I'll attach an accel file, unpack, put in ~/.config/nautilus in place of the empty one. Then either quit & restart nautilus or just log out/in 
(to quit nautilus run nautilus -q in terminal, then restart from Places > Home Folder
Then with focus on your home folder or any nautilus window go ctrl+p & see if preferences open.

---

### Post by mark bower on 2015-04-28
More explanation.  Infact the . . . nautilus/accels file is loaded with entries on my PC 15.04 and the one with the deficiency.  I found the line you highlighted, less the entry "<Primary>p".  Is the idea that I edit the highlighted line and enter "<Primary>p?  So no need to send a file. I do not see any entry saying "; user set ones can't have that." if that is important?

It is on my PC computer with 12.04 for which there are no entries in the ..nautilus/accels file.  Sorry took a confusing jaunt here.  Actually, I will do what you suggest on a laptop with 15.04 to verify, before doing it on the PC.

---

### Post by mc4man on 2015-04-28
Yes, the line should look like in my 1st gedit screen, ie this
```
(gtk_accel_path "<Actions>/ShellActions/Preferences" "<Primary>p")
```

So you need to add the <Primary>p & backspace the ; away.
See again in screen
If you leave the ; then the line change will be ignored... or set back to the default of no binding ""

Note you are free to use any binding you want as long as it's not currently used, Primary in the accels file is ctrl on the keyboard

---

### Post by mark bower on 2015-04-28
mc4man

Bingo - works like a champ!  You nailed it but good.  To summarize case someone else looks at this thread:

Case where Ubuntu 15.04 is installed, then the Desktop is modified with gnome-session-flashback, and the previous utility called Files Preference was a feature you liked to use with Nautilus(now Files).  Then:

1) gedit ~./config/nautilus/accels
2) scroll to line which reads '  ; gtk_accel_path "<Actions>/ShellActions/Preferences" "")
3) change line to read '   gtk_accel_path "<Actions>/ShellActions/Preferences" "<Primary>p")     and note that the leading ";" is removed
4) close and reboot
5) use Ctrl-p when Files(Nautilus) is opened to see and use the familiar Files Preferences pop-up.

mc4man - than you very much, this allows me (at least for now) to continue to use the desktop and files management to my liking.

---

### Post by mc4man on 2015-04-28
Glad you got it - 
Ot - 
If your Arcadia is the one I remember from ages ago, was an interesting place just south of oregon. Spent several weeks helping someone care-taking an indian cemetery near the shore,  building some driftwood items for a bit of a hut in return for shelter & food. Good days indeed..

---

### Post by mark bower on 2015-04-29
So there are two options in Files Preferences I consider essential, and one convenient to be able to do:

- display folders in List form vs Icon form
- set the behavior (File Management Preferences>Behavior>[check "Run executable text files when they are opened"]) so I can execute script files on the Desktop without having to enter the password for root
- access the resizing capability of Files Preferences, useful in the List mode so that more folders/files can be displayed vertically, yet maintain the same screen resolution.

Nope, I'm stuck in the Arcadia next to Pasadena CA.

---

### Post by craig20 on 2015-12-22
> **mark bower said:**
> o.k., the following command line looks to do the trick, I tested it twice.  But what a nuisance how Nautilus was changed for use with Gnome Classic!  I am not marking thread as solved as I am guessing there may be more negative issues to resolve. 

```
gsettings set org.gnome.nautilus.preferences default-folder-viewer 'list-view'

```
The link which uncovered the above CLI command:

[https://wiki.archlinux.org/index.php/GNOME_Files#Change_default_item_view](https://wiki.archlinux.org/index.php/GNOME_Files#Change_default_item_view)


This worked for me!  Thanks so much!!

---

### Post by richardbrucebaxter on 2016-06-21
Note the ability to modify file manager preferences is not a feature, it is mandatory.

The accels workaround (Ctrl-p) doesn't appear to work on UB16 (at least not without a restart).

---

