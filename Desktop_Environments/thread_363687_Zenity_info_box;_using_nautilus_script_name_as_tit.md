---
title: "Zenity info box; using nautilus script name as title"
date: 2007-02-17
forum: Desktop Environments
---

### Post by Keith_Beef on 2007-02-17
I'm trying to use zenity to pop up an info box when a nautilus script has finished working.

This is a small script to rotate image files, so often I will launch this script on a slew of files, then pull another window to the foreground and let it work. I'd like an alert to show me when it's finished.

I know I can add this line:
```
zenity --info --title="Finished" --text="Finished. \n Click on OK to dismiss."
```

I have several similar, but slightly different scripts.

I know, I could change the title and message text in each, to announce clearly which script has finished, but I would prefer to have a standard call using something like the bash underscore variable, i.e.:
```
zenity --info --title="Finished doing $_" --text="Finished doing $_. \n Click on OK to dismiss."
```

But this catches the last filename in the list $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS.

Now, I suppose I could set a variable at the beginning of my script, like 
```
cmd="resize_to_50%"
```
and then use 
```
zenity --info --title="Finished doing $cmd" --text="Finished doing $cmd. \n Click on OK to dismiss."
```

This gets me a unified zenity call that I can use in each script, but still requires setting a variable (I suppose I should call it a constant, since it's not changed anytime in the program once it's set).

But I would rather catch just the filename (not the full path to the filename) from a nautilus or command line variable.

Is this possible?

Thanks,
Beef.

---

