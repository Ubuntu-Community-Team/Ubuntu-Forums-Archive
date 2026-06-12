---
title: "Cannot add Desktops"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by jjmatt on 2007-09-27
I recently upgraded from Feisty to Gusty (from fresh). When I start up there is only one desktop available to me and right clicking and going to preferences doesnt yeild any options to add more. Can anyone help?

---

### Post by Rupertronco on 2007-09-28
That may have to do with the compiz-fusion enabled by default. It works with only one desktop then draws the other 3 and puts them on a cube. Do you have compiz turned on?

---

### Post by jjmatt on 2007-09-28
Ya, I meant to add that. Without compiz, this isn't a problem, I can add as many as I want. With compiz, I am stuck with only one, with seemingly no option to add more.

---

### Post by jjmatt on 2007-09-29
For anyone that may potentially be reading this:

Do not try to edit it with gconf-editor. Leave that number of workspaces at 1, if you add more, you will be going around compiz and will run into problems, as it creates its own desktops differently from gnome as Rupertronco said. 

Go to the compizconfig settings manager (ccsm in terminal) and click the only option in the general tab. On the second tab from the left I believe it is called ..., there are three options. Horizontal ... Vertical .. and Number of workspaces. Leave the number of workspaces alone and increase the Horizontal .. (or Vertical .., if you prefer) to add desktops.

---

### Post by KumoriJinsoku on 2008-01-06
I found this to be the easiest.

If you don't have it up, add Workspace Switcher to your gnome panel (and if you don't use Gnome Panel, add it... don't worry it will be temporary).

Right click on your workspace switcher, and click Preferences.

A small window should come up with Workspaces and input for Columns and Rows. Right now, I have 4 column(s) and 1 row(s).

Add more workspaces by increasing the amount of Columns. You can also do this with Rows. For example, I added two desktops by changing my 4 columns to 6.

Click close and your done. If you no longer want the Workspace Switcher up, you can remove it from the panel (and for those who don't want the panel, you may remove it as well). This also works for those who want more desktops in CompizFusion as well.

---

### Post by nisarg on 2008-04-06
This doesnt seem to work for me.
Changing the rows/columns from the workspace-switcher applet doesnt seem to make any difference. I still only see 2 desktops.
I can switch Visual Effects to NONE, then Workspace-Switcher-> Preferences shows the no. of workspaces field.

Any ideas?
Thanks.

---

### Post by reponzo01 on 2008-04-07
> **nisarg said:**
> This doesnt seem to work for me.
Changing the rows/columns from the workspace-switcher applet doesnt seem to make any difference. I still only see 2 desktops.
I can switch Visual Effects to NONE, then Workspace-Switcher-> Preferences shows the no. of workspaces field.

Any ideas?
Thanks.

What worked for me is the following:

sudo gconf-editor

Then navigate to apps->compiz->general->screen0->options. In options, right-click on "hsize", click on Edit Key and change from "2" to "4". Close your way out of that. Then right-click a desktop box (lower right corner of your desktop) and go to Preferences. Change the Columns from "2" to "4". Hope that works!

---

### Post by nisarg on 2008-04-07
Thanks

> **reponzo01 said:**
> What worked for me is the following:

sudo gconf-editor

Then navigate to apps->compiz->general->screen0->options. In options, right-click on "hsize", click on Edit Key and change from "2" to "4". Close your way out of that. Then right-click a desktop box (lower right corner of your desktop) and go to Preferences. Change the Columns from "2" to "4". Hope that works!

---

