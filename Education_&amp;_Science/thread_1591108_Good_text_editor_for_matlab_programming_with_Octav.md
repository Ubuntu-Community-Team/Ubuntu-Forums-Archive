---
title: "Good text editor for matlab programming with Octave"
date: 2010-10-08
forum: Education &amp; Science
---

### Post by vacco on 2010-10-08
Does anyone know of a good text editor for matlab programming?

I am currently using gedit for the purpose, but I am missing some handy functions like line numbering and subsequent lines getting the same indent as current upon hitting return (a function I have when using Octave with Textpad in Windows).

Also, gedit's color coding in .m files does not appear to be 100% good.

I am sure emacs is bound to come up as a suggestion, but for a beginner like me, it seems much too advanced :(

---

### Post by radioboy on 2010-10-08
You can set up all that (but maybe not a better highlighting) in gedit preferences.
Also check the gedit-plugins package. You will be able to activate them in 
Preferences->plugins.
Another good editor is Kate (although I haven't tried Matlab code), if you don't mind installing some kde libraries if you're running Gnome.

---

### Post by radioboy on 2010-10-08
Here is a Matlab-syntax-highlighting-defintion-addon for Kate:

[http://search.cpan.org/~szabgab/Syntax-Highlight-Engine-Kate-0.06/lib/Syntax/Highlight/Engine/Kate/Matlab.pm]("http://search.cpan.org/~szabgab/Syntax-Highlight-Engine-Kate-0.06/lib/Syntax/Highlight/Engine/Kate/Matlab.pm")

Edit: for gedit, check the following links; the threads are worth reading completely.
[http://blogs.ethz.ch/ubuntu/2007/06/05/matlab-part-2/]("http://blogs.ethz.ch/ubuntu/2007/06/05/matlab-part-2/")
[http://ubuntuforums.org/showthread.php?t=368353]("http://ubuntuforums.org/showthread.php?t=368353")
[https://bugs.launchpad.net/ubuntu/+source/gtksourceview2/+bug/418199]("https://bugs.launchpad.net/ubuntu/+source/gtksourceview2/+bug/418199")
Be sure to read comment 8:
[https://bugzilla.gnome.org/show_bug.cgi?id=170604]("https://bugzilla.gnome.org/show_bug.cgi?id=170604")

---

### Post by vacco on 2010-10-08
Thank you very much! I ended up on the gedit solution.

The link [http://ubuntuforums.org/showthread.php?t=368353](http://ubuntuforums.org/showthread.php?t=368353) was very useful.

Other than that, the solution to most of my questions were no worse than actually looking in gedit's user preferences (guess I should have done that first, sorry).

Lots of useful goodies in the plugin package though. Too bad the embedded terminal does not run Octave automatically :P Otherwise quite ingenious :D

---

### Post by gunksta on 2010-10-08
Linux is full of text editors. If programming/text editing is something you will be doing a lot, learning one (or both) of the biggies will be useful. EMACS and Vim. Yes, the learning curve is worth it **IF** you do enough editing. If this is for a freshman EE class and you have to write some stuff in Matlab and you don't really intend to do much more than that -- skip 'em. They only become useful if you A) use them often and B) use them for nearly everything.

Whatever you do, choose a general purpose text editor. Gedit is actually a pretty nice tool. It is very multi-purpose and can handle syntax highlighting for a large number of languages. Don't waste your time learning a fancy tool that really only works well with one or two languages, unless someone pays you to.

Other alternatives:

[Geany]("http://www.geany.org/Main/AllFiletypes")
Netbeans, via a [plugin]("https://octavenb.dev.java.net/"). (This is an IDE, not a text editor.)
[QTOctave]("http://qtoctave.wordpress.com/what-is-qtoctave/") (Only useful for Matlab/Octave programming)

[Monkey Analytics]("http://www.monkeyanalytics.com/") (Not OSS, but awfully interesting)

---

### Post by matthew.ball on 2010-10-09
> **vacco said:**
> I am sure emacs is bound to come up as a suggestion, but for a beginner like me, it seems much too advanced :(
Nah, don't worry. It's not too advanced, and certainly if you're a beginner the earlier you pick it up the better it will be in the long run.

If you're interested, I can send you a rather in-depth Emacs cheat-sheet I wrote for a workshop I did. While it doesn't cover Octave (though there iss really nice Octave integration in Emacs), it does cover a lot which I couldn't find in other cheat-sheets.

Really, just go through the tutorial once, it'll take maybe 20 minutes. You'll be fine, it's not too difficult to pick up. It will become really natural after a while (a week of use I would estimate), it can seem a bit overwhelming at first, but there are lots of places you can ask questions if you ever get stuck.

There's the old saying "learn one editor, and learn it well". If you ever find yourself programming, writing LaTeX documents or customising your GNU/Linux system, it can all be done consistently in the one editor.

---

### Post by frozenmaple on 2013-04-29
> **matthew.ball said:**
> Nah, don't worry. It's not too advanced, and certainly if you're a beginner the earlier you pick it up the better it will be in the long run.

If you're interested, I can send you a rather in-depth Emacs cheat-sheet I wrote for a workshop I did. While it doesn't cover Octave (though there iss really nice Octave integration in Emacs), it does cover a lot which I couldn't find in other cheat-sheets.

Really, just go through the tutorial once, it'll take maybe 20 minutes. You'll be fine, it's not too difficult to pick up. It will become really natural after a while (a week of use I would estimate), it can seem a bit overwhelming at first, but there are lots of places you can ask questions if you ever get stuck.

There's the old saying "learn one editor, and learn it well". If you ever find yourself programming, writing LaTeX documents or customising your GNU/Linux system, it can all be done consistently in the one editor.

Could you send the sheet to me ? i send my mailbox to you in private message, thx~

---

### Post by crislosi on 2013-12-16
There is another alternative, it is SublimeText with SublimeREPL plugin. With the plugin you can execute Octave from SublimeText.
And another one is Cantor, a kde program. You can install it from Ubuntu repos.

---

### Post by PC_load_letter on 2013-12-30
[Octave 3.8 now comes with a native GUI]("http://ubuntuforums.org/showthread.php?t=2196608"), and an editor. It's very similar to the Qt version.

My personal favorite is still Geany. Although I am tempted now to use the native editor in Octave for debugging.

---

