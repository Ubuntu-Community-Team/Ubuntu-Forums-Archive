---
title: "Problem with GNU Screen when using control + arrows"
date: 2009-12-06
forum: Education &amp; Science
---

### Post by Makmiller on 2009-12-06
Hi all, 

I've been having the following problem with GNU Screen. I like using Ctrl + left/right arrows to move between words but it sometimes doesn't work if I'm within GNU Screen.  More specifically, I noticed the following: 

**1.** When I'm at the terminal prompt inside of GNU Screen, I can move between words using Ctrl + arrows without any problem. However,  if I call Emacs (with the command "emacs-snapshot-gtk -nw"), and I press Ctrl-<right> I get the characters "5D." I get the characters "5C" when I press Ctrl-<left>. 

**2.** When I'm outside of GNU Screen and I call Emacs from the terminal, I do **not** have this problem with the Ctrl key. 

Do you know how I can solve this problem?


Thanks very much!

Note: I'm using emacs 23.1 and gnome-terminal.

---

### Post by gunksta on 2009-12-07
I'll admit it - when I started using screen heavily, I stopped using emacs. Screen gave me the thing I liked most about EMACS, so I found them to be a little repetitive. Thanks to jalvesaq's  r-plugin for vim, I was able to stop using emacs altogether.

That being said. . . . . 

I do know that Screen uses the control key (specificiall CTRL+A) for many of it's key bindings and EMACS uses the CTRL key to start many of it's key bindings.

This _could_ be a conflict between screen and emacs. Have you tried remapping the CTRL key in emacs to something random (CAPS is a popular option) to see if that fixes the conflict? I realize this is probably not a "fix" but it could be used to isolate the source of the problem.

Conversely, you might want to make sure that both emacs and screen are using / assuming they are in the same type of terminal.

---

### Post by Makmiller on 2009-12-08
> **gunksta said:**
> I'll admit it - when I started using screen heavily, I stopped using emacs. Screen gave me the thing I liked most about EMACS, so I found them to be a little repetitive. Thanks to jalvesaq's  r-plugin for vim, I was able to stop using emacs altogether.

That being said. . . . . 

I do know that Screen uses the control key (specificiall CTRL+A) for many of it's key bindings and EMACS uses the CTRL key to start many of it's key bindings.

This _could_ be a conflict between screen and emacs. Have you tried remapping the CTRL key in emacs to something random (CAPS is a popular option) to see if that fixes the conflict? I realize this is probably not a "fix" but it could be used to isolate the source of the problem.

Conversely, you might want to make sure that both emacs and screen are using / assuming they are in the same type of terminal.

Thanks very much for your suggestion gunksta!  I've just started playing with gnu screen but I've been really enjoying its Emacs-like features. 

I just have a further question: if the problem I'm having is bc of a conflict because of the use of  ctrl in both gnu screen and emacs, then I think I should assign, say, caps lock as control key **only** for emacs. Do you know how I can I do this? (i.e. I found instructions to swap ctrl and caps lock that would work for every application) Another possibility would be to assign a modifier key to gnu screen other than ctrl, but I don't think this is possible... am I wrong about this?

Cheers,

---

### Post by gunksta on 2009-12-08
There are a couple of options you could consider.

First, there's an extension for Emacs called [Viper Mode]("http://www.emacswiki.org/emacs/ViperMode"). It lets you use vi shortcuts for most common tasks. But, I'm not sure that would address your problem. Read [this]("http://www.emacswiki.org/emacs/MovingTheCtrlKey") to learn how to remap your CTRL Key to the CAPS key.

In my experience, screen and Vim go together like a hand and a glove. I found that using Emacs with screen was repetitive. For example, Emacs can run multiple, simultaneous, buffers that are actually terminal emulators. While this is incredibly useful by itself, it is repetitive when used in conjunction with screen.

Thus - more proof that emacs is not a text editor. It is actually an operating system with a really good default text editor.  :-)

---

### Post by Makmiller on 2009-12-08
Hi gunksta,

> **gunksta said:**
>  Read [this]("http://www.emacswiki.org/emacs/MovingTheCtrlKey") to learn how to remap your CTRL Key to the CAPS key.


the strategies at the emacs wiki swap control and caps to every application (including GNU Screen), isn't it? Or am I missing something here?

> **gunksta said:**
>  I found that using Emacs with screen was repetitive. For example, Emacs can run multiple, simultaneous, buffers that are actually terminal emulators. While this is incredibly useful by itself, it is repetitive when used in conjunction with screen.

This is a good point... At least in my little experience with GNU Screen, I saw myself constantly trying to use Emacs shortcuts with GNU Screen -- and vice versa. It was a mess sometimes :) 

About the possibility of switching to Vim, I don't know much about Vim, but there are some features in Emacs that I really like other than the possibility of having multiple buffers. One of them is the extension to LaTeX, the AUCTeX, which allows you to have a preview of some parts of your document (e.g. equations) in the source buffer.  The other cool extension is the org-mode.  But, of course, given my lack of knowledge about Vim, I bet Vim has some really nice features as well...

Thanks for your help! 

Cheers,

mak

---

### Post by gunksta on 2009-12-10
I could have sworn there was a way to remap the CTRL key in your .emacs file, but apparently I made that up to confuse you.  :-)  Sorry about that. I googled for a way to do it and I failed. Unfortunately, my .emacs got deleted the last time I cleaned up my sync system.

Regarding Vim v. EMACS - There's no such thing as the "perfect" tool. Here's a quick comparison of the best thing about both tools: The neat thing about EMACS is that it wants to do EVERYTHING the EMACS way, which is terrific. The neat thing about Vim is that it wants to do everything the Unix way, which is also neat (and available everywhere). People have debated which is best for years - and since there is no actual answer people are still arguing about it.

My LATEX skills are super-amateur-hour, so I won't even try to compare Vim to EMACS for LATEX editing, but I do know there are some Vim extensions specifically for this. 

Vim does have the Vim Outliner which is similar to org-mode if you need to write outlines and stuff like that, but it lacks some of the spreadsheet-like capabilities that org-mode included which I confess were really really cool. Vim's tool can export to LATEX and HTML but I don't think it's quite as flexible as org-mode in terms of output. On the plus side, it's super fast and easy to use.

If I bump into anything about how to edit the .emacs file to move the CTRL key I'll let you know.

---

### Post by Makmiller on 2009-12-10
I posted this problem I'm having to the GNU Screen forum and they found a workaround. In case someone else runs into the same problem, control and shift keys will work as usual within emacs provided that you locally change the value of the TERM variable (within GNU Screen) to "xterm." The complete thread is available at

[http://www.mail-archive.com/screen-users@gnu.org/msg02752.html]("http://http://www.mail-archive.com/screen-users@gnu.org/msg02752.html")

And thanks gunksta for your help. I should definitely give a try to Vim. 

Cheers,

mak

---

