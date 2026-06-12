---
title: "What are the '~' files? (Screenshot)"
date: 2009-01-29
forum: Desktop Environments
---

### Post by sharathpaps on 2009-01-29
When I use 'ls' to list files, the output lists files with a symbol '~' at the end (screenshot). In windows I know that these represented files that are currently being edited or something like that. But here these files are not being edited. I already saved the files and moved them elsewhere. They are not hidden but I still can't see them on the Desktop. I'm just being curious.

Thank You

---

### Post by kaivalagi on 2009-01-29
> **sharathpaps said:**
> When I use 'ls' to list files, the output lists files with a symbol '~' at the end (screenshot). In windows I know that these represented files that are currently being edited or something like that. But here these files are not being edited. I already saved the files and moved them elsewhere. They are not hidden but I still can't see them on the Desktop. I'm just being curious.

Thank You

Files with a tilde "~" on the end are the old versions of the files you edited. Some apps (not all) keep a backup file like this. You can probably delete them if you're happy with the ones you've moved.

---

### Post by mcduck on 2009-01-29
Most commonly you'll get those files when you edit some text document with Gedit. you can simply turn off this feature in Gedit's settings if you don't want backup versions..

---

### Post by sharathpaps on 2009-01-29
@mcduck: how do I access gedit settings. Is there any harm in turning this feature off?


@kaivalagi: I tried removing the files using Terminal, but I get an error message. (Screenshot) . I can't delete using the GUI because the files are not visible on the Desktop. They are not hidden anyway.

Sorry for my ignorance. Still very new to Ubuntu.

Thank You.

---

### Post by mcduck on 2009-01-29
> **sharathpaps said:**
> @mcduck: how do I access gedit settings. Is there any harm in turning this feature off?


@kaivalagi: I tried removing the files using Terminal, but I get an error message. (Screenshot) . I can't delete using the GUI because the files are not visible on the Desktop. They are not hidden anyway.

Sorry for my ignorance. Still very new to Ubuntu.

Thank You.

In Gedit, Edit/Preferences. The setting is on "Editor"-tab, just disable the "Create a backup copy of files before saving"-option.

(In case you didn't know, gedit is the default text editor in Gnome)

The files _are_ hidden. By default the file manager hides both dotfiles and backup files. Press Ctrl-h to show them (or enable showing hidden files in file manager's preferences).

The reason why your "rm" command didn't work is that there's a space in the file's name. The command you used tells rm to remove two files, one called "La" and one called "Femme~". You have to tell rm that these two separate words are part of the same file's name:
```
rm "La Femme~"
```

---

### Post by sharathpaps on 2009-01-29
@mcduck 

Thank You, I managed to find and delete those files... :-)

---

### Post by kaivalagi on 2009-01-29
> **sharathpaps said:**
> @mcduck 

Thank You, I managed to find and delete those files... :-)

In the terminal you should try using the <TAB> feature for auto-completion, it will handle file names with spaces for you

So if you typed "rm La" then hit <TAB> you should see it complete it for it so it looks like this "rm LA\ Femme~"

You may have to hit TAB twice, I can't remember, I am currently at work using windows :(

Have fun :)

---

### Post by sharathpaps on 2009-01-29
@kaivalagi : Hi, thanks for the tip. I'd read it somewhere else but couldn't remember it.. Now I won't forget :-)

---

