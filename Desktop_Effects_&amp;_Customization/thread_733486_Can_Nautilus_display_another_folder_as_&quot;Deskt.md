---
title: "Can Nautilus display another folder as &quot;Desktop&quot;?"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by tomjennings on 2008-03-23
I want nautilus to display a directory of my choosing as the "desktop". I can find no way to do this. It of course displays the contents of ~/Desktop on the screen; if that's rmdir'd it shows ~/ (home).

Is there a way to set this to something else?

---

### Post by carrett on 2008-03-23
Unfortunately I think the main choices are ~/Desktop or just ~ (if you set desktop_is_home_dir in /apps/nautilus/preferences in gconf-editor). You could try tricking nautilus by making a symlink called ~/Desktop that points to whatever dir you want (ln -s /the/dir/you/want ~/Desktop). Let me know how that goes. It doesn't seem to work for me.

Best of luck.

---

### Post by tomjennings on 2008-03-23
> **carrett said:**
>  You could try tricking nautilus by making a symlink called ~/Desktop that points to whatever dir you want (ln -s /the/dir/you/want ~/Desktop). 

Forgot to say -- I tried that. Doesn't work. It's one of those rare hard-coded features.


Generally speaking, I dislike the "desktop" paradigm, I generally just don't run nautilus. But on my music/DJ machine it migt be useful to have my music collection/folders as "desktop".

The problem with putting that stuff in a dir named "Desktop" is that stupid name has all sorts of desktop-y baggage and behavior associated with it (download default, "Trash" nonsense, etc) and I just am not down with this Windows and Apple nonsense.

Oh well, I'll probably just kill nautilus off again. Thanks for the suggestion though!

---

### Post by Ocxic on 2008-03-24
sudo mount -o bind /your_perferred_desktop_directory /home/user/Desktop

---

### Post by tomjennings on 2008-03-24
> **Ocxic said:**
> sudo mount -o bind /your_perferred_desktop_directory /home/user/Desktop

omigod that's pure madness... :-) 

Alas, it still would not do the job -- which is to not use ~/Desktop as a name... that's increasingly a magic name for where browsers and other things dump files. 

"Desktop" carries with it meaning, is the core problem... 

Thanks though!

---

