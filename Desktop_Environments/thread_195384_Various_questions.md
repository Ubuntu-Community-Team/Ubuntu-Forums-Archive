---
title: "Various questions"
date: 2006-06-12
forum: Desktop Environments
---

### Post by keke21 on 2006-06-12
Sorry if any of these have been posted before and/or are in the Wiki. Also, these questions are all over the place. They pretty much list everything I couldn't figure out on my own within an hour.

#1: Is there any way to make GRUB detect keyboard input so that I can hold a key to make the menu come up? I'd prefer that the computer just boot into Ubuntu automatically unless I need to do something in another operating system.

#2: Is there any way to prevent Windows from installing its own bootloader over GRUB? I know how to recover GRUB, but it's still annoying to have Windows taking over the boot sector.

#3: Is there any way to make window borders larger/smaller? "Panels" lets you resize each panel pixel-by-pixel. Anything like that for window borders?

#4: Any way to make the panels mimic the theme I.E. I like the orange gradient on the windows, so can my panels do the same?

#5: Every new user I have starts out with the volume set to be *really* loud (71?). Can I change the default volume?

Thanks.

---

### Post by keke21 on 2006-06-13
#6: Is there any way to make the mouse move faster without increasing acceleration? I'm used to the slightest twitch moving the mouse halfway across the screen.

---

### Post by keke21 on 2006-06-13
Anyone?

I've been looking these up, and I still can't find them.

---

### Post by beameup on 2006-06-13
I can comment on a couple of these.

#1: Yes you can edit the GRUB config file to set the amount of time the selection window shows up or if you want it to show up at all. I'd have to search the forum for specific instructions.

#2: Unfortunately Windows will always take over the boot sector. You'll have to install it first or continue the recovery process.

---

### Post by jrd on 2006-06-13
You can change the default window time for grub by editing /boot/grub/menu.lst.
This is the part you edit```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4
```
In this case it would show up for 4 seconds.

---

### Post by scxtt on 2006-06-14
[QUOTE=keke21]

#1: Is there any way to make GRUB detect keyboard input so that I can hold a key to make the menu come up? I'd prefer that the computer just boot into Ubuntu automatically unless I need to do something in another operating system.[/quote]you can use the code below in menu.lst to bypass the menu all together - maybe set the timeout to 3 seconds ...

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

> #2: Is there any way to prevent Windows from installing its own bootloader over GRUB? I know how to recover GRUB, but it's still annoying to have Windows taking over the boot sector.install windows 1st (or on a separate drive) then it's a non-issue ...

> #3: Is there any way to make window borders larger/smaller? "Panels" lets you resize each panel pixel-by-pixel. Anything like that for window borders?probably only by editing the source for the "window border" in the theme ...

> #4: Any way to make the panels mimic the theme I.E. I like the orange gradient on the windows, so can my panels do the same?same as #3 ...

> #5: Every new user I have starts out with the volume set to be *really* loud (71?). Can I change the default volume?doubtful ... you *might* be able to pass some sort of command-line option when installing, but i doubt it ... and there are simple solutions (like keeping speakers off on 1st boot, boot into safe mode and edit conf file) ...

---

### Post by keke21 on 2006-06-14
Alright. These answers were helpful. For #5, scxtt said *exactly* what I needed. It's not new computers that bother me, but new users (I would like to see the volume turned down a little someday, though). Perfect answer.

Too bad about the panels' look and the window border size. Same for Windows installing NTLDR over GRUB. I wish operating systems weren't so adament about using their own bootloaders.

#1, though, I think I said what I meant incorrectly. I have the timeout to one second at the moment, so the only way I can get it to show for any useful amount of time is to hold the down-arrow key. Is there any way where GRUB will detect other input, such as the spacebar or the m key?

---

