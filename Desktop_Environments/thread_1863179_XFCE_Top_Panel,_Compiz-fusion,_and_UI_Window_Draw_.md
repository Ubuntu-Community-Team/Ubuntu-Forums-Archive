---
title: "XFCE Top Panel, Compiz-fusion, and UI Window Draw Annoyance."
date: 2011-10-17
forum: Desktop Environments
---

### Post by Adam_GUI on 2011-10-17
This is probably more than two problems.

Had the dist-upgrade from 11.04 to 11.10 the other day.
Now running XFCE 4.8 as a UI.

On my desktop, I have a single xfce panel on the top border.
When launching some programs, the UI will draw them as such that the top of the window, where min, max, and close are, will be behind the panel.

This only happens when compiz is enabled.
When I set fusion-icon to use metacity or Xfwm4, the title border is drawn just below the panel, rather than behind it.  (as preferred).

I found a "work around" that is supposed to allow UI draws over the panel in xfce.

```
xfconf-query -c xfce4-panel -p /panels/panel-0/disable-struts -t bool -n -s true

```

But, it isn't a catch all.  Some programs will draw over the panel.  Others, namely mozilla's firefox and thunderbird, continue to draw beheath the panel.  Pretty sure this is a compiz setting I've missed.

Is there a Compiz settings manager option I can use to tell compiz not to draw in the top 35 set range reserved for the xfce panel?

As an aside, using emerald instead of gtk-window-decorator removes my ability to right click a program's edge and select "move".  Using gtk-window-decorator --replace restores the menu.  So, if there's an emerald workaround for that...

**FIX IN POST #7** [Thanks, paul.bono]("http://ubuntuforums.org/showpost.php?p=11674816&postcount=7").

---

### Post by ankspo71 on 2011-10-18
Hi,
It has been a while since I've used compiz, so I don't know if it has a setting like that, but there is an XFCE setting that can do what you need, and I think it will work with Compiz too. Go to Settings > Settings Manager > Workspaces. Look at the diagram on the right. That is where you can set a top margin (a space on the desktop that no window can cover). Make the top number 35 or so. The setting should take effect immediately.

---

### Post by Adam_GUI on 2011-10-18
Good try. No go.
I set a margin draw at a match to my panel.
Window titles and buttons are still being drawn underneath the panel by compiz.  So, it's not a pure xfce issue.  

Compiz ignores the panel as a no-draw area and treats it as "always on top" on program screen draws.

So, any program that draws along the top or top left ends up with titles beneath the xfce panel with compiz enabled.  It does this same action using emerald or gtk-window-decorator.

Disabling compiz and using xfwm4 results in normal behavior with title bars drawn just under the panel, treating it as a "no-draw" area.

I have not had this issue or similar since moving the panel to the bottom of the screen.

So, I've regained workability by moving the xfce panel and switching my avant manager to the side until I find or get recommended a fix that works.

---

### Post by djahma on 2011-10-20
I faced a similar window problem with compiz some time ago, and I believe I sorted the problem by switching on some options within ccsm window section. sorry for not being more accurate:-\

---

### Post by Adam_GUI on 2011-10-26
The problem is still the same.
I've since moved on to KDE and am using kwin instead of emerald.

Leaving the thread here, but I'm moving to greener pastures.

Not sure how to mark a thread status to anything other than open.

---

### Post by mrnatas20 on 2011-12-18
In CCSM, under Effects, make sure "Window Decorations" is enabled

---

### Post by paul.bono on 2012-02-09
I fixed this problem by setting a place window rule.

Settings > CompizConfig Settings > Window Management > Place Windows

I enabled this and then went into the setting's "Fixed Window Placement" tab and added "class=Xfce4-panel" using maximize mode.

This causes the new windows to load towards the bottom of the screen.

Hope this helps anyone looking to fix the XFCE and Compiz window issue.

---

### Post by Adam_GUI on 2012-02-09
> **paul.bono said:**
> I fixed this problem by setting a place window rule.

Settings > CompizConfig Settings > Window Management > Place Windows

I enabled this and then went into the setting's "Fixed Window Placement" tab and added "class=Xfce4-panel" using maximize mode.

This causes the new windows to load towards the bottom of the screen.

Hope this helps anyone looking to fix the XFCE and Compiz window issue.

Whoa!  That's got it.  Though, I set things to smart mode instead of maximize.  The UI border is no longer being drawn beneath the top screen xfce panel.

Thanks!

---

### Post by pfindan on 2012-05-21
Thank you so much! Looked all over for this!

Now enjoying wobbly windows with compiz in 12.04!

---

### Post by rylleman on 2012-06-01
I also have this problem. Opening apps below the xfce bar is not such a big problem for me however. My problem is that when I use compiz fullscreen mode (Extra WM Actions) some applications is fullscreened behind the xfce panel. 
Most works well but some, wine-apps is where I've encountered it, suffers from this.

As I want them fullscreen none of the tips above is applicable.

---

### Post by rrosinski on 2012-07-08
Thank You!

The Place Windows trick worked!
Would have never have found this.

---

