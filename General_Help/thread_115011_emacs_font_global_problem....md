---
title: "emacs font global problem..."
date: 2006-01-09
forum: General Help
---

### Post by string on 2006-01-09
Hi,

I have a problem. When I ran a Gentoo, my emacs had smoooth awesome fonts.
But now with kubuntu, it doesn't.

I'm no specialist in emacs customizing but ... as those things were there right after the installation of emacs, I have really no idea how to fix it ...

Here are 2 screenshots of what I have and what I used to have... :

[IMG]http://latex.tugraz.at/emacs_nocolor_full.png[/IMG]
That was the cool one.
[IMG]http://www.debianusers.pl/articles/resources/emacs-devel/emacs-devel.png[/IMG]
And this is the crappy one I woud like to get rid of...

Thanks

---

### Post by frootstripe on 2006-01-09
So you want to turn off highlighting? From the emacs manual:

Font Lock mode
==============

   Font Lock mode is a minor mode, always local to a particular buffer, which highlights (or "fontifies") using various faces according to the syntax of the text you are editing.  It can recognize comments and strings in most languages; in several languages, it can also recognize and properly highlight various other important constructs--for example, names of functions being defined or reserved keywords.

   The command `M-x font-lock-mode' turns Font Lock mode on or off according to the argument, and toggles the mode when it has no argument. The function `turn-on-font-lock' unconditionally enables Font Lock mode.  This is useful in mode-hook functions.  For example, to enable Font Lock mode whenever you edit a C file, you can do this:

     (add-hook 'c-mode-hook 'turn-on-font-lock)

You want find out how to change fonts and display within emacs??
Type the following within emacs:

C-h i d m  emacs <return> i faces <return>

**note that display customization information will be the previous node in regards to the one you will be taken to by typing the command above.

This key sequence can be used as above to read about any subject in the emacs manual, (of course, the term "faces" above would be substituted for the keyword you wished to research.

from there you'll have to read the documentation to discover what specifically you can and can't do.

From the manual:

"When using Emacs with a window system, you can set up multiple styles of displaying characters.  Each style is called a "face".  Each face can specify various attributes, such as the height, weight and slant of the characters, the foreground and background color, and underlining.  But it does not have to specify all of them.

---

### Post by string on 2006-01-10
It's not the highlighting, it the very font, on the first screenshot, it is small and cool, on the second one, it is big and not cool :/ ...

---

### Post by frootstripe on 2006-01-10
a quick fix to adjust the size of emacs font, is to, within the emacs window you are working in, apply the following key sequence:

Shift-<left mouse button>

This will give you a popup menu that allows you to choose various font options, including decreasing font size.

Permanently changing the default font obtions is more complicated but can be done - through reading the emacs manual and the "introduction to elisp", the latter can be obtained at gnu.org in their documentation section.

---

