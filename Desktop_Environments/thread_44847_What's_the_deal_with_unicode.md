---
title: "What's the deal with unicode?"
date: 2005-06-27
forum: Desktop Environments
---

### Post by rosslaird on 2005-06-27
I've searched the forums, and there seems to be no straightforward solution to what I'm thinking of a simple problem (or maybe I'm just too dumb to see the solution).

I want to be able to see the extended unicode characters (the "digraphs" in vim, like em dashes and typographic quotations marks) when I ctrl-alt-f1 to a virtual console. Currently I see little boxes instead of the characters. I've tried "unicode_start" which gives me "already in utf8 mode". Now that can't be right, can it? If it was, I'd see the characters properly, wouldn't I?

Or maybe I'm going about this the wrong way. I just want to see the damned characters properly.

Ross

---

### Post by rosslaird on 2005-06-27
OK, I found this, from here: [http://www.jw-stumpel.nl/stestu.html#T4.7](http://www.jw-stumpel.nl/stestu.html#T4.7)

> There is very little support for Unicode on the console. There is a command called unicode_start, the man page of which says

    The unicode_start command puts both the screen and the keyboard in Unicode mode [..] 

But, in fact, it seems that this command (which you can undo with unicode_stop) only puts the screen into UTF-8 mode. E.g., the UTF-8 character é (=hex C3 A9) is correctly displayed (if you have a console font which has the é). But typing the é will not work. And console fonts can have only a very limited number (256, or, at a pinch, 512) of characters, so full Unicode support seems difficult, to say the least.

The subject of ‘console support for Unicode’ comes up regularly on the linux-utf8 mailing list. It seems that to make it work, extensive changes in (in fact, large additions to) the kernel would be needed. This simply does not seem worth the effort. So don’t count on real Unicode support for the console very soon. Run your Unicode text-mode programs in X, using xterm, which has good Unicode support.
UTF-8 ‘console’ support requires framebuffer

The consensus now seems to be: the actual Linux console is a terminal device. You could, and I once actually did this as an experiment, control a Linux system through a ‘dumb terminal’ connected to a serial port. You could probably use an old ASR 33 Teletype if you really had to. But it would be unreasonable to expect an ASR 33 to print the Unicode character repertoire. The same applies to the ordinary console support provided by the kernel. The kernel will provide you with ‘emergency’ services, in case the system is in trouble and you want to connect in single-user mode. You should not expect anything more.

People who do insist on ‘console’ support for Unicode should provide for it in user space, not kernel space. Various projects for doing just that, based on using a framebuffer console, are actually under way, see, for instance, here. But IMHO, if you can do framebuffer then you could just as well do X.


I suppose this means that I'm basically out of luck.

---

### Post by bogdanb on 2008-02-15
There are two parts to your problem: displaying characters and typing them. 

For displaying, there is a partial solution: The standard console fonts only contain a very limited set of characters, usually only a bit more than ASCII (I think é and è are usually included, but not typographic quotes). You can change the console font to one that has more useful characters.

First you need the console-setup package. AFAIK it's always installed by default, if not you need to install it yourself ("sudo apt-get install console-setup").

Then you need to edit the file /etc/default/console-setup. The setting FONTFACE picks which font to use; I use Terminus because it has many characters and I think it's pretty, but the shapes of the letters are quite different than the default and it may annoy you.

I think you also need to change the CODESET. As far as I know, Uni3 is the biggest. (But keep in mind that it can only show a few hundred characters, so don't expect seeing Japanese there without some heavy hacking.)

Look in /usr/share/doc/console-setup at the README.fonts file for more info.

After you pick your settings and write them in /etc/default/console-setup, you'll need to run "sudo setupcon --save"; this prepares everything to load the chosen font at startup. The next time you reboot you should see the new font and the pretty characters. (Be careful to run these in a console, not in an X terminal, because they like to argue and it might fail. Be ready for some debugging, in any case.)

If you want to type funny characters in the console, you can do it from the same /etc/default/console-setup file, by changing the various XKB* options to pick another layout.

Good luck!

---

### Post by bogdanb on 2008-02-15
After a bit more experimentation, it turnes out that you could also use Uni2 with the VGA font. This looks very just like the default font plus the extra characters. (Though I still like Terminus better.)

This includes most latin characters, including â&#537;&#539;&#259;îðæœþ–Â&#536;&#538;&#258;ÎÐÆŒÞS—„”«»&#8804;&#8805;!¡?¿÷²³€×&#8800;µéèÉÈáàäëïíìúùü&#363;&#299;&#257;&#333;&#275;.txt and a lot other, which is not bad.

---

