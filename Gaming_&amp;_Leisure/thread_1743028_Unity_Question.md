---
title: "Unity Question"
date: 2011-04-29
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2011-04-29
So, Im trying out 11.04 with the unity interface.  I know this isnt really a game question per se, but it applies to games, and this section of the forum is usually the most helpful.

In the old interface, I could create a menu icon to launch a game, for my example NWN.  With unity, I dont want a NWN icon on the panel itself since its just too space limited, but I want it to show up when I search for installed applications.  Any idea how to do this?  I've tried a few things, but without any luck

---

### Post by oedipuss on 2011-04-29
My guess would be creating a .desktop file in /usr/share/applications 

Trying that now with a dummy file to see if it works.

Edit: aaand it works =) 
You can look up the syntax [here]("http://developer.gnome.org/integration-guide/stable/desktop-files.html.en"), or just copy an existing launcher and adjust it.

 I'm not sure if this is the best way, though.

---

### Post by Naegling23 on 2011-04-29
bingo

thanks, but wow, what a pain.  I figured since I'll likely do this a bunch of times, I just changed permissions to usr/share/applications, but there should be an easier way to do this

---

### Post by oedipuss on 2011-04-29
On second thought maybe it would be best to use ~/.local/share/applications instead, if unity sees it.

Have you tried just creating the launcher the old way, even if it can't be used as is? Presumably that would still create a desktop file.

---

### Post by keltic dave on 2011-04-29
search for main menu then just add a new application launcher were every you want it. You can then have it pop up in a search.

---

### Post by Pierrick584 on 2011-04-30
> **keltic dave said:**
> search for main menu then just add a new application launcher were every you want it. You can then have it pop up in a search.


as he said, and to make it clear in case it was not for some, the menu you get from the button "super" contain every single item of the old school menu, so there is no difference at all, beside how you see them :)

---

### Post by mpfleger on 2011-05-01
I've tried the .desktop file thing using the gimp one as a reference, but I have a few questions:
1) what to do with the StartupNotify option?
2) what does the "Exec=gimp-2.6 %U" field mean? the multiple URL reference on the Gnome integration guide isn't really that illuminating... is there a nice concise explanation as to how this relates to the executable being called?
3) how critical is MimeType? I'm doing this for gtkwave, whose package unsurprisingly doesn't come with a .desktop (or a .png, but I found that one online so whatever), so I put the following in there:
MimeType=application/vcd;
-but I don't know if this is the correct syntax in this case...

Any clarification/insights would be greatly appreciated.

PS I'm pretty OK with what I've seen with Unity so far, but *this* particular issue, in particular with putting together .desktop files for things that don't come with them (and thus can't be found by searching) is something that needs some degree of automation or streamlining. Just my $.02

Cheers,
M

---

