---
title: "Gedit Html-Tidy"
date: 2009-02-17
forum: General Help
---

### Post by dringof1 on 2009-02-17
Hi,

I'm using Ubuntu 8.10 and Gedit 2.24.2. I am trying to use the html tidy plug-in but it crashes Gedit. I have added the plugin in the .gnome2/gedit/plugins/ folder and all the file and folder permissions seem ok.
When I load up Gedit and go to preferences > plugins the html-tidy plugin is displayed, its just when I click on it Gedit crashes.
The output from the terminal is as followed:

```
WARNING -  raising exception can't find data directory
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/html-tidy/plugin.py", line 51, in __init__
    self._data_dir = gen_utils.data_dir()
  File "/usr/lib/gedit-2/plugins/html-tidy/gen_utils.py", line 108, in data_dir
    raise ex.error('can\'t find data directory')	
html-tidy.ex.error: "can't find data directory"
Segmentation fault
```

So im guessing by the output that the path to the data directory can't be found. I have installed as suggested so im not sure how to fix.

Any help is much appreciated.

Thanks.

---

### Post by Tibuda on 2009-02-17
I don't use this plugin. Instead I add a custom tool to the "external tools" plugin. The tool I add just calls Tidy in the current file:```
#!/bin/sh
zenity --question --title="Tidy" --text="Reformat document?"
if [ "$?" = 0 ]; then
  tidy -q -m -i -w 80 "$GEDIT_CURRENT_DOCUMENT_PATH"
else
  tidy -q -e "$GEDIT_CURRENT_DOCUMENT_PATH"
fi
```

---

### Post by dringof1 on 2009-02-17
Hey thanks for the reply. Yeah that seems to work nicely!!! Thanks! Do you know of a way to validate the document when its via FTP? Cheers.

---

### Post by fragos on 2009-02-17
> **danielrmt said:**
> I don't use this plugin. Instead I add a custom tool to the "external tools" plugin. The tool I add just calls Tidy in the current file:```
#!/bin/sh
zenity --question --title="Tidy" --text="Reformat document?"
if [ "$?" = 0 ]; then
  tidy -q -m -i -w 80 "$GEDIT_CURRENT_DOCUMENT_PATH"
else
  tidy -q -e "$GEDIT_CURRENT_DOCUMENT_PATH"
fi
```

This works but I want to look at the output become making the change. Tidy to a new gedit tab would be ideal for me. Gedit documentation gives a list of the variables but doesn't explain them. To be honest the differences between them are unclear to me. Any help clearing my haze would be appreciated.

---

### Post by Mr Fredrick on 2009-05-21
I have the same problem as the OP.

Does anybody have any further suggestions as to how to get the Tidy plug-in to work correctly with gedit?  That is other than the work-round already given.

Thanks in advance,

Mr Fred.

---

### Post by grimdestripador on 2010-12-02
Found this on google search. and Here we are at Ubuntu 10.10 and this is still unanswered. I have added plugins everywhere. it can't find the data directory either.

---

