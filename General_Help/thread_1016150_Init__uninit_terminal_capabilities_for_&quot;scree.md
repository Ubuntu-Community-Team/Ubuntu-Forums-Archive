---
title: "Init / uninit terminal capabilities for &quot;screen&quot;"
date: 2008-12-19
forum: General Help
---

### Post by barrkel on 2008-12-19
When I'm running programs (such as **less**) inside **screen** that normally initialize and uninitialize the terminal (in the [termcap sense]("http://www.gnu.org/software/termutils/manual/termcap-1.3/html_chapter/termcap_4.html#SEC39")), the contents of the terminal window are not saved and restored.

Concrete example:

[LIST=1]
[*]Start screen
[*]Run e.g. less, with man less (normally less is the viewer for man)
[*]Quit less with 'q'
[*]Observe that contents of less manpage are still visible, and the prior contents of the terminal window are lost
[/LIST]

When performing the same sequence of steps **outside** of **screen**, things work as expected. If starting from a cleared terminal window, this is what appears:

```

~$ man less
~$ 

```

Whereas when the steps are followed inside **screen**, it looks more like this:

```

...
       SPACE or ^V or f or ^F
              Scroll  forward  N  lines,  default  one  window (see option -z below).  If N is more than the
              screen size, only the final screenful is displayed.  Warning: some systems use ^V as a special
              literalization character.

       z      Like SPACE, but if N is specified, it becomes the new window size.

~$ 

```

(with the cursor at the bottom of the terminal window.)

How can I get screen to work more like a normal, more fully-featured terminal?

(It's desperately hard to search for such generic terms as "less terminal screen initialization" and get specific help about the screen program... :( )

---

