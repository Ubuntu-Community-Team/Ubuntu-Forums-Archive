---
title: "One more Xfce question -- menu options"
date: 2012-08-01
forum: Desktop Environments
---

### Post by vasa1 on 2012-08-01
I asked a question about getting Thunar to offer an option to open a folder of songs with a music player [here]("http://ubuntuforums.org/showthread.php?p=12144062#post12144062").

Now, I've got a similar question but I don't know if it involves Thunar or not.

I've set up an Xfce 4.10 panel to give me a sort of "launcher" on the left side of the screen. It appears on hover and I have my most used apps there.

The question is about the folder named [FONT="Courier New"]Songs[/FONT]. If I single-click it, I get two options, [FONT="Courier New"]open folder[/FONT] and [FONT="Courier New"]open in terminal[/FONT].

Is it possible to add a third option: [FONT="Courier New"]open with Totem[/FONT]? For that matter, is it possible to remove [FONT="Courier New"]open in terminal[/FONT] in this case?

---

### Post by LewisTM on 2012-08-01
Hello again!

The Directory menu plugin has limited options, I don't think you can set custom commands for it.
The best you could do is make a launcher with command
```
totem /home/<you>/Songs
```
Remember you can make a launcher that contains a collection of sub-launchers. You can use that in conjunction with [FONT="Courier New"]totem --enqueue <dir> [/FONT]or [FONT="Courier New"]totem --replace <dir> [/FONT]commands to populate your playlist.

Cheers!

---

### Post by vasa1 on 2012-08-01
> **LewisTM said:**
> Hello again!

The Directory menu plugin has limited options, I don't think you can set custom commands for it.
The best you could do is make a launcher with command
```
totem /home/<you>/Songs
```
Remember you can make a launcher that contains a collection of sub-launchers. You can use that in conjunction with [FONT="Courier New"]totem --enqueue <dir> [/FONT]or [FONT="Courier New"]totem --replace <dir> [/FONT]commands to populate your playlist.

Cheers!

I didn't even know that it's called the "directory menu plugin"!

It looks like the sub-launcher route may be the way to go.
But this is new stuff to me and it's late here. I'll look at it tomorrow.

Thanks once again :)

---

### Post by vasa1 on 2012-08-02
Well, I've done my best and this is the "hack" I came up with.

First, I added a new item (launcher) to my vertical panel.
Second, I edited it ...
[INDENT]Name: Music[/INDENT]
[INDENT]Command: none (I couldn't create the launcher without entering something so I entered "none")
[/INDENT][INDENT]Icon: as shown[/INDENT]
Third, I added subsequent items named after various folders, with the command of the type [FONT="Courier New"]totem /home/username/Music/subfolder_name[/FONT]

So now I have a dummy launcher which unsurprisingly throws up an error if I left-click it ;)
and I have the actual "sublaunchers" which work as intended.

I'm content with what I have but if there's a proper, or better, way rather than what I've done, do let me know.

Thank you for the pointers and I'm marking this one "solved" :)

---

### Post by LewisTM on 2012-08-02
Yeah, that's pretty much the idea.
You can use a dummy command like [FONT="Courier New"]echo[/FONT] for your top launcher so you don't get errors.

---

### Post by vasa1 on 2012-08-02
> **LewisTM said:**
> Yeah, that's pretty much the idea.
You can use a dummy command like [FONT="Courier New"]echo[/FONT] for your top launcher so you don't get errors.

Done. Thanks!

---

### Post by vasa1 on 2012-08-03
I came across a [tutorial]("http://community.linuxmint.com/tutorial/view/164") which shows how to fit the arrow into what I called the dummy in my previous post. This simplifies things in that there's now no need of having a dummy command. Clicking on the (previously) dummy button which now has the arrow within it gives a dropdown of all the music folders.
Here's a quote from the tutorial:
> 
[10]. Now the FINAL step... by default there should be a little arrow next to the magnifying glass icon and if you click on it your newly created snappy launcher with drop down with all your menu item. Personally, I don't like the arrow and I rather click on the icon itself to make the list drop down. So do this>>>
[11]. Highlight your icon on the panel, right click and select "Properties". THEN in the dialog box, look ON TOP of the box with all your launchers and you'll see the word "Arrow:" and a drop down box that says "Default". Click on it and select the bottom option "Inside Button" then hit OK.

It's probably for an earlier Xfce but now the setting is in the **advanced** tab.

---

