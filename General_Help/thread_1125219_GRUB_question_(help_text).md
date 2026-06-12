---
title: "GRUB question (help text)"
date: 2009-04-14
forum: General Help
---

### Post by Rikki123s on 2009-04-14
Hey everyone,

I was wondering if it is possible at all to remove the help text from the GRUB menu (the text that says:

Use the [up] and [down] keys to select which entry is highlighted.
Press Enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for a command-line.

), I basically have a background image in my GRUB boot loader menu and that text just gets in the way.

Hope someone can help.

---

### Post by askreet on 2009-04-14
It seems like you can either hide, or not hide, the menu:

[http://www.gnu.org/software/grub/manual/grub.html#hiddenmenu](http://www.gnu.org/software/grub/manual/grub.html#hiddenmenu)

---

### Post by Rikki123s on 2009-04-14
I do want the menu there, I just don't want the help text. is there like a text file that contains the help text (so I can delete the text)?

---

### Post by askreet on 2009-04-14
> **Rikki123s said:**
> I do want the menu there, I just don't want the help text. is there like a text file that contains the help text (so I can delete the text)?

It's probably compiled in, GRUB is loaded into the MBR so they likely avoid loading help text from an external source.  I think you're outta luck for removing that text.

---

### Post by stchman on 2009-04-14
> **Rikki123s said:**
> Hey everyone,

I was wondering if it is possible at all to remove the help text from the GRUB menu (the text that says:

Use the [up] and [down] keys to select which entry is highlighted.
Press Enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for a command-line.

), I basically have a background image in my GRUB boot loader menu and that text just gets in the way.

Hope someone can help.

Set the timer to zero so you don't have to look at GRUB at all.

---

### Post by budmanca on 2009-07-10
Actually the text "Use the &#8593; and &#8595; keys to select which entry is highlighted. Press enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for a command line." is located in the stage2 file. You will need a hex editor and root privileges. I use ghex it's in the ubuntu repositories. In a terminal type "sudo apt-get install ghex" without the quotes to install ghex, then type "sudo nautilus" to open nautilus with root privileges. In the filesystem go to /boot/grub and make a backup copy of stage2 just in case, then right click on stage2 and select "open with other application" and choose hex editor. The text your looking for is close to the bottom of the file. You'll be able to read it on the right side. When you find it double click on the first letter of it and then replace all the letters with a space and save the file. DO NOT DELETE THE LETTERS If you do you won't be able to boot. On mine I had to replace the "." right before the text and the one right after as they print on the screen also. Hope this helps. Now if anybody that knows more about this can tell me how to get rid of the white border around the operating systems my grub will look great! [-o<

---

