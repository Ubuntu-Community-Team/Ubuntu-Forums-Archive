---
title: "Gedit LaTeX"
date: 2012-07-05
forum: Desktop Environments
---

### Post by eloydark on 2012-07-05
I want to make the transition and use gedit as my main latex editor, but I am having a problem that prevents me from doing it.

I am using the Cobalt theme in gedit

when I use the "\label" command, the background color changes (not only in cobalt, it changes in all themes) to FFFFCF thus rendering the text unreadable (FFFFFF)

I tried editing the cobalt.xml GtkSourceView but found no style utilizing the FFFFCF color code. Further googling revealed that the FFFFCF code is used in the "warning-background-color" parameter. Is there a workaround to fix this issue without having to recompile gedit from source?

I find it strange that noone has ever had the same error that I have encountered.

---

### Post by eloydark on 2012-07-06
Found the solution after a bit of more searching!

sudo gedit /usr/share/glib-2.0/schemas/org.gnome.gedit.plugins.latex.gschema.xml

then find the warning-background-color and change the color to your liking

---

### Post by eloydark on 2012-07-06
Correction:
This solution appeared to work fine until I turned on the Latex Plugin in gedit.
Now the background changes to ffffcf in \label and changes back when I turn off the plugin.
Very frustrating bug...
I searched the .py files in /usr/share/gedit/plugins/latex and /usr/lib/gedit/plugins/latex and found no mention of ffffcf so it must be somewhere else...
Any suggestions?

---

### Post by carandraug on 2013-01-14
> **eloydark said:**
> Correction:
This solution appeared to work fine until I turned on the Latex Plugin in gedit.
Now the background changes to ffffcf in \label and changes back when I turn off the plugin.
Very frustrating bug...
I searched the .py files in /usr/share/gedit/plugins/latex and /usr/lib/gedit/plugins/latex and found no mention of ffffcf so it must be somewhere else...
Any suggestions?

I'm trying the same thing. This can be changed on the file

```
/usr/lib/gedit/plugins/latex/latex/editor.py
```

Somewhere there is the lines

```

        self.register_marker_type("latex-error", self._preferences.get("error-background-color"))
        self.register_marker_type("latex-warning", self._preferences.get("warning-background-color"))

```

the part ```
self._preferences.get("warning-background-color")
``` specifies the color to use.

But I think there's a deeper issue here. Why is it marking the labels and refs as warnings? Is it warning us for some bad LaTeX practice or is it parsing something badly and thinks we are doing something wrong?

---

### Post by carandraug on 2013-01-14
I have opened 2 bug reports against the plugin:

[LIST]
[*][unreferenced labels should not be highlight as warnings]("https://bugzilla.gnome.org/show_bug.cgi?id=691758")
[*][warnings same color independent of style used]("https://bugzilla.gnome.org/show_bug.cgi?id=691757")
[/LIST]

To solve your problem, I'd recommend to do what I suggested on the first bug report, to comment line 89 of the latex/latex/validator.py which goes like:

```

issue_handler.issue(Issue("Label <b>%s</b> is never used" % escape(label.value), label.start, label.end, label.file, Issue.SEVERITY_WARNING))

```

This line says that non referenced labels should be highlighted as warnings. I disagree (specially because I reference them on unusual ways) and don't think it should so I just commented the line. Works fine now

---

