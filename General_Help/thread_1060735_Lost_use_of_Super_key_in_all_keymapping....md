---
title: "Lost use of Super key in all keymapping..."
date: 2009-02-05
forum: General Help
---

### Post by inspired on 2009-02-05
Hi folks,
I had a keymap of Super+space which would pull up gnome-do. Gnome-do set this when I installed it and ticked the preference related to this.

Today I used the built in Keymapping tool in Ubuntu to change some other keymap. I noticed I was not able to get the Super key to work. Meaning, if I assigned a Super+(a key) to a mapping, that mapping would not work. So I gave up on trying to do what I wanted.

Then, after closing the keymapping editor, none of Super key maps work, including the Super+space for gnome-do. I have set gnome-do to use a different mapping (works fine immediately) and then changed it back to the original <Super>Space and it won't work.

Also if I edit the keymaps in the Configuration Editor (for metacity) using the <Super> command does not work.

Any ideas?

I'd really like to sort this out as I typically use Super in my keybindings as it's usually such a safe bet in terms of not interferring with anything else. Now it's busterated.

Cheers,

Jonathan

PS. As aside... How can I mark threads as SOLVED? There is no option in the Thread Tools when I look there.

---

### Post by inspired on 2009-02-05
I should add that I have found if I add <Alt>, for instance, to the binding then it will work. So, for instance, <Super><Alt>j will work, but just <Super>j will not work.
And it is not that the Super key is being ignored, because I can assign one thing to <Alt>j and a different thing to <Super><Alt>j.
Both will work.

---

### Post by inspired on 2009-02-12
I have not managed to resolve this. My windows/super key is dead as far as keymappings go. I'd really like to fix it as most of my keymappings used the windows/super key.

Anyone?

Thanks...

Jonathan

---

### Post by inspired on 2009-02-26
Hi folks,
Well, I never did manage to figure this out. It still drives me a little nuts, being such a big user of the Super key and all.

This is a bump... to say I am still wanting to solve this and any help would be gratefully appreciated.

Cheers,
Jonathan   :popcorn:

---

### Post by Pyronhell on 2009-02-28
Hi!

I had exactly the same problem as you. In my case, I have noticed that none of the <Super> keybindings on the gnome keymap editor works, so I have changed it to other keys (Instead of <Super>L, <Ctrl><Alt>L or similar, not using <Super>), and now I have the Gnome-Do working.

---

### Post by inspired on 2009-05-15
I think I pretty much figured this one out.
There was some kind of conflict between the various way key shortcuts can be set. They can be set in Compiz and also in Gnome config directly, and with the gnome Keyboard Shortcuts tool, and even with other tools.

I removed all instances of Super being specified in the Keyboard Shortcuts app. I then only have them assigned in CompizConfig.

As far as I can tell, there is a bug. It seems that if I have a shortcut in Keyboard Shortcuts that uses the Super key, this stops the superkey from working.

---

### Post by kanikilu on 2009-05-15
> **inspired said:**
> As far as I can tell, there is a bug. It seems that if I have a shortcut in Keyboard Shortcuts that uses the Super key, this stops the superkey from working. I'm not sure if that's the case. I have shortcuts in the Gnome keyboard settings, as well as Compiz that use Super+<SingleCharacter>.

Have you tried playing with the Alt/Win key options in the keyboard layout?

System > Preferences > Keyboard > Layouts > Layout Options > Alt/Win key behavior is set to "Meta is mapped to Win keys" for me. On one of my other computers, though, I had to set it to "Meta is mapped to Left Win".

---

