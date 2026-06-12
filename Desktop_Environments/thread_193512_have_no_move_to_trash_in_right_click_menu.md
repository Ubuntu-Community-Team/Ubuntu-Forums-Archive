---
title: "have no move to trash in right click menu"
date: 2006-06-10
forum: Desktop Environments
---

### Post by gumara on 2006-06-10
i use xubuntu dapper on ibook g4 12"

in the right click menu have a delete button. but have no move to trash.

---

### Post by BitTorrentBuddha on 2006-06-10
EDIT: Didn't catch the XFCE tag

---

### Post by lepre on 2006-07-04
[QUOTE=gumara]i use xubuntu dapper on ibook g4 12"

in the right click menu have a delete button. but have no move to trash.[/QUOTE]

there's not a trash in xfce yet :neutral:

---

### Post by lapsey on 2006-07-06
[QUOTE=lepre]there's not a trash in xfce yet :neutral:[/QUOTE]

but there can be if you: 

mkdir ~/.Trash

and then create a custom action with something like "mv %thisfile ~/.Trash"

it's worth a try

---

### Post by Jucato on 2006-07-06
How exactly could you "create a custom action" in Xfce??

---

### Post by lepre on 2006-07-06
[QUOTE=lapsey]but there can be if you: 

mkdir ~/.Trash

and then create a custom action with something like "mv %thisfile ~/.Trash"

it's worth a try[/QUOTE]

that's interesting, i thought about doing something similar, but i wasn't able to do it in xfce..

if you can tell us something more we'd like :KS

---

### Post by lapsey on 2006-07-09
sorry for the late response. thunar allows the custom actions:
 
[http://thunar.xfce.org/plugins.html#thunar-uca](http://thunar.xfce.org/plugins.html#thunar-uca)



a further recommendation is to create a panel launcher that contains the command "thunar ~/.Trash" or "thunar /home/myhome/.Trash", as to open the trash :)

---

### Post by Jucato on 2006-07-10
@lapsey: Thanks for the link and for the idea. I made a very short tutorial on how I was able to add a right-click Trash context menu in Xubuntu.

HOWTO: Add a right-click "Move to Trash" context menu in Xubuntu
NOTE: Using Thunar only

1. **Create a hidden directory in your home folder named** **.Trash**: Right-click on an empty space in your Home folder and choose "Create Folder". In the "Enter the new name" field, type in *.Trash* (Don't forget the dot/period at the beginning to make it a hidden directory).
2. **Make a new Custom Action:**
- In the Edit menu, choose "Configure custom actions..."
- Click on the + button at the right to make a new custom action
- In the Basic tab, enter the following in the appropriate fields:
**Name:** Move to Trash
**Description:** (enter anything you want)
**Command:** mv %N ~/.Trash (at the bottom of the dialog box, there are explanations of the the various % arguments are)
**Icon:** (anything you want)
- In the Appearance Conditions tab, check everything and make sure that File Pattern is set to "*" (minus the quotes).
- Click on OK, then Close

Screenshots: (This is on a VMWare Server session)
NOTE: I reduced the screenshots to 640x480 for bandwidth reasons. But I can upload the full 1024x768 if somebody needs them.

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntutrash1.jpg[/IMG]

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntutrash2.jpg[/IMG]

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntutrash3.jpg[/IMG]

[IMG]http://i73.photobucket.com/albums/i206/jucato/screenshots/xubuntutrash4.jpg[/IMG]

---

### Post by lapsey on 2006-07-10
> **Fenyx said:**
> @lapsey: Thanks for the link and for the idea. I made a very short tutorial on how I was able to add a right-click Trash context menu in Xubuntu.

very nice! I should point out that if you try to trash an item with the same name as an existing folder in .Trash , mv will fail. 

[http://unixhelp.ed.ac.uk/CGI/man-cgi?mv](http://unixhelp.ed.ac.uk/CGI/man-cgi?mv)

Nautilus currently renames the files "%filename (Nth copy).extension". Not bad, but it modifies the filename which can be confusing in some situations and the only benefit is seeing the files in one folder.

So the best solution I can think of is to move the files into a timestamped folder: 

t=$((`date -u +%Y%m%d%H%m%S`)) ; mkdir ~/.Trash/$t ; mv %N ~/.Trash/$t

hopfully this command should work (NB: it doesn't!)

---

### Post by Jucato on 2006-07-10
Wow, I never knew about that. Good thing I didn't make a HOWTO thread about it. I think I'm satisfied that I was able to go that far. Of course the solution that we presented are just workarounds. Nothing beats a real trash handling/management feature. 

Until that comes around, I might be staying away from Xubuntu for the mean time.

Btw, I heard that Trash management is a feature/function of the File Manager, which, in this case, is Thunar. Does the previous Xfce file manager, ROX-Filer, have Trash management? Is there anyway I could make that the default file manager instead of Thunar? :D

(Actually I can't believe that the Xubuntu devs would actually be using a "half-baked" system, since Xfce 4.4 is still in beta AFAIK. And Thunar is not that complete yet either)

---

### Post by lepre on 2006-07-11
there's a little problem...because i'm used to delete files with the del key..it's possible to make a workaround about this?

---

