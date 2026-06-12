---
title: "&quot;Could not add application to application database&quot;"
date: 2005-05-30
forum: Desktop Environments
---

### Post by NeoChaosX on 2005-05-30
Hey, I'm trying to change the default video player to be VLC. But in Nautilus, whenever I try to select VLC, I get this error message:

"Could not add application
Could not add application to application database"

Does anyone know what's going on here and how to fix it?

---

### Post by aetherane on 2005-08-27
I am having the same issue, has any solution been found?

---

### Post by Icaros on 2005-08-28
I'm getting this problem as well.  I can't change associations of any type without getting that error.

---

### Post by pmj on 2005-08-28
I have no idea what is causing this, but you can associate video files to VLC if you instead of choosing VLC for Gtk+ in the list you click "Use a custom command" and type "vlc".

---

### Post by arnieboy on 2005-08-28
[QUOTE=NeoChaosX]Hey, I'm trying to change the default video player to be VLC. But in Nautilus, whenever I try to select VLC, I get this error message:

"Could not add application
Could not add application to application database"

Does anyone know what's going on here and how to fix it?[/QUOTE]
Try the following:
```
rm $HOME/.local/share/applications/* 2>/dev/null
killall nautilus
```
now try adding default apps again.

---

### Post by Icaros on 2005-08-28
Nice fix!  I was trying to associate mp3's with beep mp and wasn't able to... Now my mp3's play in beep.  Thanks!

New problem though, with php files, I want them to open with the text editor, but they default with OpenOffice.  When I select Properties->Open With I see the radio button for text editor, but it won't let me select it.  Any ideas?

EDIT: For some reason, Lock Screen has become the equivelant to ALT+CTRL+BACKSPACE after applying your suggestion.

---

### Post by mcduck on 2005-08-30
[QUOTE=arnieboy]Try the following:
```
rm $HOME/.local/share/applications/* 2>/dev/null
killall nautilus
```
now try adding default apps again.[/QUOTE]
I'm having the same problem, I can't change any default applications. Your tip didn't work but I noticed that .local in my home directory is owned by root. (Should it be?) So I tried what you told to do, this time with sudo. Didn't work either. Then I removed the whole .locale, and after killall nautilus nothing has changed..

Any ideas what's wrong and how I could fix this problem?

---

### Post by arnieboy on 2005-08-30
[QUOTE=mcduck]I'm having the same problem, I can't change any default applications. Your tip didn't work but I noticed that .local in my home directory is owned by root. (Should it be?) So I tried what you told to do, this time with sudo. Didn't work either. Then I removed the whole .locale, and after killall nautilus nothing has changed..

Any ideas what's wrong and how I could fix this problem?[/QUOTE]
guys, i will look into this problem when i get back home tonight to my ubuntu box. hopefully we will have a solution

---

### Post by mcduck on 2005-08-30
Thanks, now it worked. For some reason removing the directory with that command didn't work, but i did 'sudo nautilus' and deleted my .locale from there. That worked, so my problem's solved now. (I still don't know why your command didn't work, or how my .locale and everything in it even got owned by root in first place)

Thanks for your tip. I think I'll write it down somewhere as long as I don't know how to avoid this happening again..

---

### Post by Icaros on 2005-08-30
Did you do anything else when you were removing .locale?

That trick didn't work for me...  Whenever I try "Open With" from Properties, I can see other programs to select from, but they simply cannot be selected.  I'm sudo nautilus'ing this thing, too.

---

### Post by mcduck on 2005-08-30
No, that's all I did. (I also logged in and out and restarted X couple of times while I tried to solve the problem, but I don't think that helped anything as I did'n do any of those after I removed the folder with nautilus).

I think my problem was wrong ownership of .locale, you can easily check if you have same problem. Just right-click the folder and check properties/permissions and File Owner & File Group. I don't know how that happened, maybe some update broke it or something.

I could select the applications from list, and I could (try to) use my own command, but clicking Open only gave me same error message that NeoChaosX got. If you problems are related to something else, I don't think I can help. It seems that arnieboy knows a lot more about these things, so maybe he finds out something..

---

### Post by arnieboy on 2005-08-31
[QUOTE=mcduck]No, that's all I did. (I also logged in and out and restarted X couple of times while I tried to solve the problem, but I don't think that helped anything as I did'n do any of those after I removed the folder with nautilus).

I think my problem was wrong ownership of .locale, you can easily check if you have same problem. Just right-click the folder and check properties/permissions and File Owner & File Group. I don't know how that happened, maybe some update broke it or something.

I could select the applications from list, and I could (try to) use my own command, but clicking Open only gave me same error message that NeoChaosX got. If you problems are related to something else, I don't think I can help. It seems that arnieboy knows a lot more about these things, so maybe he finds out something..[/QUOTE]
mcduck I just got back home and looked into the problem. what u said is absolutely right. $HOME/.locale should be owned by your user account NOT root, because otherwise everytime u try to assign a default app to open a kind of file, it will not be able to write that info in the $HOME/.local/share/applications directory (where it stores this information) cuz the owner of the folder is root!
good to know that u figured it out urself before I had to look into it :)

---

### Post by Ensnared on 2005-09-17
I'm having this exact same problem and the fixes here doesn't work. The weird thing is, it's only VLC that gives this error, all other applications are added as one would expect, so it doesn't appear to be a problem with the permissions on the directories but the application itself.

What I notice is that there are files placed in the ~/.local/share/applications/ named gvlc-something.desktop, while the actual comman to run vlc is wxvlc (there is no gvlc command). Could that have something to do with it?

---

