---
title: "make new icons automatically add to right side instead of left side of desktop"
date: 2010-12-18
forum: Desktop Environments
---

### Post by oarion7 on 2010-12-18
If a file gets created in the user's Desktop folder, or if a drive is added to the machine and a Desktop icon is correspondingly created, they will by default appear on the left side of the desktop (unless, in the case of the latter, the specific drive has been created before and dragged to the right side, in which case GNOME will remember to put it in the same place).

Because I have a terminal window embedded onto my Desktop in the top left corner and occupying most of the screen), I keep my icons on the right side of the Desktop instead of the left (Mac style) - Any time I add a new drive or a file is sent to the Desktop, however, I have to kill the terminal window to be able to click on the icon, then drag it back to the right side, then restart the terminal.

Is there any way to tweak GNOME so that these icons are added from the top right corner and down instead of from the top left, automatically?

Regards,

Ryan:popcorn:

---

### Post by 3Miro on 2010-12-18
To your question: I don't know.

However, you can try to create a bunch of useless shortcuts to take up the entire row on the left, so that the terminal will cover those and the removable media icons will be placed further to the right. I hope this is clear.

You can also go to Places -> Removable Media. Or Places -> Home and you should have shortcuts for your drives on the left (it is one more click, but it may work for you).

PS You can look into gconf-editor for more settings. Hit Alt + F2 and type
[CODE]gconf-editor[\CODE]
the settings for the icons should be associated with nautilus.

---

### Post by oarion7 on 2010-12-18
> **3Miro said:**
> To your question: I don't know.

However, you can try to create a bunch of useless shortcuts to take up the entire row on the left, so that the terminal will cover those and the removable media icons will be placed further to the right. I hope this is clear.

Interesting work around; I had not thought of that. The only issue other than that fix seeming a little "unclean" is that the terminal is *transparent* so that the desktop background shows through underneath.

I have looked at gconf-editor a bit; hopefully there is someone who knows it inside and out and maybe there is a way to change the direction of icon arrangement in there. Either that, or we could find some way to make a section of the desktop inaccessible to icons so that they begin piling up only in the space after the terminal has ended.... I'll keep looking.

Anyone who might be able to help, please leave a note! I am sure there is someone else who would be interested in this hack.

**EDIT: Is there any way anyone can think of to specify a grid of space on the desktop in which icons must not appear? Even if they align from left to right after that point? (e.g. the last two columns of desktop space)**

or

Is there a way to take the right-to-left icon feature of the Arabic and Hebrew Ubuntu configurations and somehow apply that to Desktop icons only?

---

### Post by 3Miro on 2010-12-18
You can put the text on the shortcut to be only one character long (i.e. a dot .) and you can pick a small icon like classviewer-var (it seems one of the smallest on my list, but you may have different ones). Unfortunately, I don't has Gnome right now, so I cannot tell you about gconf-editor. I am afraid that the option that you need may not be implemented even in the Arabic versions.

---

### Post by asmoore82 on 2010-12-18
I can't offer any real help :cry:, but I though you might like to know
that there is a longstanding Gnome bug on this issue. I can't remember
all of the gory details, but the developers do want to fix this and
it *should be* easy but it is not - due to some underlying design
assumptions in the codebase that need to be re-architect-ed.

---

### Post by oarion7 on 2010-12-28
[This guy (link)]("http://www.linuxquestions.org/questions/programming-9/nautilus-desktop-icons-righ-to-left-402227/") proposed a way of possibly going about it from the source code, but was not really sure how to continue: 

> **"3saul"]I'm wanting to change the lay down code for the desktop only so that icons on the nautilus desktop are layed down right to left instead of left to right (or rather top to bottom right to left). Just like on the Mac. I don't want other nautilus windows to be affected (ie stay the same left to right). I found this code in nautilus-icon-container.c

static void
lay_down_icons (NautilusIconContainer *container, GList *icons, double
start_y)
{
switch (container->details->layout_mode)
{
case NAUTILUS_ICON_LAYOUT_L_R_T_B:
lay_down_icons_horizontal (container, icons, start_y) said:**
> static void
icon_container_set_workarea (NautilusIconContainer *icon_container,
GdkScreen *screen,
long *workareas,
int n_items)
{
int left, right, top, bottom;
int screen_width, screen_height;
int i;

left = right = top = bottom = 0;

screen_width = gdk_screen_get_width (screen);
screen_height = gdk_screen_get_height (screen);

for (i = 0; i < n_items; i += 4) {
int x = workareas ;
int y = workareas [i + 1];
int width = workareas [i + 2];
int height = workareas [i + 3];

if ((x + width) > screen_width || (y + height) > screen_height)
continue;

left = MAX (left, x);
right = MAX (right, screen_width - width - x);
top = MAX (top, y);
bottom = MAX (bottom, screen_height - height - y);
}

nautilus_icon_container_set_margins (icon_container,
left, right, top, bottom);
}

I'm new to programming so if anybody could give me any pointers as to whether or not this is achievable that would be great. I've posted to the Nautilus mailing list and also searched it but got nothing.

Thanks in advance.


Any idea?

---

