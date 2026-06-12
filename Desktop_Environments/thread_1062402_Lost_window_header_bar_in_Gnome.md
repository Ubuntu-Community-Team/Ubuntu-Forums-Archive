---
title: "Lost window header bar in Gnome"
date: 2009-02-06
forum: Desktop Environments
---

### Post by tx836519 on 2009-02-06
I have a machine running Ubuntu 8.04 (Hardy Heron) that has suddenly developed a problem in Gnome.  I can open windows and run application OK, but the windows are missing the window header that usually displays the icon for window options on the left end, lists the application / open file in the center and has the Minimize/Window/Close icons on the right end.  I tried to fix this by going to System/Preferences/Windows and get the following message box:

    - Cannot start the preferences application for your windows manager.
      Window manager 'unknown' has not been registered a configuration tool.

Does anyone know what configuration file I have lost, or even better, what I need to do to fix this problem?

---

### Post by JECHO on 2009-02-06
> **tx836519 said:**
> I have a machine running Ubuntu 8.04 (Hardy Heron) that has suddenly developed a problem in Gnome.  I can open windows and run application OK, but the windows are missing the window header that usually displays the icon for window options on the left end, lists the application / open file in the center and has the Minimize/Window/Close icons on the right end.  I tried to fix this by going to System/Preferences/Windows and get the following message box:

    - Cannot start the preferences application for your windows manager.
      Window manager 'unknown' has not been registered a configuration tool.

Does anyone know what configuration file I have lost, or even better, what I need to do to fix this problem?


Boot to the desktop and press alt+f2 and type "metacity --replace" without the quotes. :)

---

### Post by tx836519 on 2009-02-06
> **JECHO said:**
> Boot to the desktop and press alt+f2 and type "metacity --replace" without the quotes. :)
At the Gnome desktop, I get no response to Alt-F2, but Cntr-Alt-F2 exits Gnome and prompts me for a text-mode login.  Is this what you want me to do?

As I pointed out above, the system is working fine in all other respects and, since it is a server for my network, I don't want to break something by going off half-prepared!  -- ken

---

### Post by Yashiro on 2009-02-06
Go into your Appearance panel and set desktop visual effects to none. Or run *metacity --replace *from a terminal.

If that fails to fix it, go into the theme panel and select the theme called Mist.

---

### Post by tx836519 on 2009-02-07
> **Yashiro said:**
> Go into your Appearance panel and set desktop visual effects to none. Or run *metacity --replace *from a terminal.

If that fails to fix it, go into the theme panel and select the theme called Mist.
Yashiro,
The appearance is already selected to 'none'.  In a text mode terminal, running

sudo metacity -- replace

gets:
'Window manager error:  Unable to open X display.'

Selecting theme 'Mist' did not fix the problem either.  -- ken

---

### Post by Yashiro on 2009-02-07
Is this at the box or via VNC?

---

### Post by tx836519 on 2009-02-07
> **Yashiro said:**
> Is this at the box or via VNC?
Yashiro,

Yes, I am at the box proper.  I do use VNC connections as well, so it is a valid question!

Thank you for your previous suggestions.  While I did not make any progress on the first attempt, I again tried switching themes (this time back to Human) and it cleared my problem.  I now have the window header and all is working well.

---

### Post by Yashiro on 2009-02-07
Good-o.

---

### Post by 4ebees on 2009-03-04
> **JECHO said:**
> Boot to the desktop and press alt+f2 and type "metacity --replace" without the quotes. :)

Thanks for that Jecho...this was driving me crazy!

---

