---
title: "html2text"
date: 2006-06-11
forum: Desktop Environments
---

### Post by jimw on 2006-06-11
I've just installed html2text.  It's there, an executable file, in /usr/bin.  However, when I try to run it in the terminal, it doesn't do anything.  Terminal just hangs, no error message, no nothing.

I wouldn't be surprised if I've missed something, or done something wrong.

Anyone have any ideas?

JimW

---

### Post by nanotube on 2006-06-11
[QUOTE=jimw]I've just installed html2text.  It's there, an executable file, in /usr/bin.  However, when I try to run it in the terminal, it doesn't do anything.  Terminal just hangs, no error message, no nothing.

I wouldn't be surprised if I've missed something, or done something wrong.

Anyone have any ideas?

JimW[/QUOTE]
it is probably expecting input from commandline, if you run it whithout any arguments. run "man html2text" to see the manual for it, it should give you an idea of how to use the program.

---

### Post by aysiu on 2006-06-11
The Synaptic description reads: > **An advanced HTML to text converter**
html2text was written because the author wasn't happy with the
output of "lynx -dump" and so he wrote something better. The only time I've heard it referenced (outside of this thread) is to allow Kat to index HTML files for search. Kat is like Beagle and Spotlight--it's a desktop search tool.

---

### Post by jimw on 2006-06-12
[QUOTE=nanotube]it is probably expecting input from commandline, if you run it whithout any arguments. run "man html2text" to see the manual for it, it should give you an idea of how to use the program.[/QUOTE]

Right.  Easy, once you know how.  Thanks a lot.

Now, do you have a notion as to how I can run this command, direct the output to the Desktop, and have it come up with a readable file?

The file I want to do this particular time is done in Cyrillic, and the output is all garbage.

I can cut and paste it from the terminal, but it would be nice to be able to output it.

What would be really nice is to have an aoo like Notepad Lite (a Windows thing) which can strip the html tags from a piece of text right there, and has the facility to save it in varous formats (.txt, .rtf, etc.)

JimW

---

### Post by nanotube on 2006-06-12
[QUOTE=jimw]Right.  Easy, once you know how.  Thanks a lot.

Now, do you have a notion as to how I can run this command, direct the output to the Desktop, and have it come up with a readable file?

The file I want to do this particular time is done in Cyrillic, and the output is all garbage.

I can cut and paste it from the terminal, but it would be nice to be able to output it.

What would be really nice is to have an aoo like Notepad Lite (a Windows thing) which can strip the html tags from a piece of text right there, and has the facility to save it in varous formats (.txt, .rtf, etc.)

JimW[/QUOTE]
to redirect this to a file on the desktop, you would use standard shell redirects. so you would do
```
html2text yourinputfile and whatever arguments html2text requires > ~/Desktop/theoutputfile.txt
```
that will automatically take all output from html2text and redirect it to theoutputfile.txt on your desktop. :)

to learn more about doing things on commandline in general (including pipes and redirects, which are quite nice), you can go to the first link in my sig, and then find the section "other commandline resources".

as to your question about the graphical editor that can stript things out... well, you could use scite, which is an editor that supports regexps in its search/replace, so you could run a simple search/replace that would replace every instance of <somestuff> with nothing, thus stripping out all html tags. 

but, html2text is just as good, and probably even better if it aims to preserve some semblance of paragraphs, etc, after stripping out the html.

---

### Post by aysiu on 2006-06-12
If you have no arguments, you can just do ```
html2text inputfile.html > outputfile.txt
```

---

### Post by jimw on 2006-06-24
[QUOTE=nanotube]to redirect this to a file on the desktop, you would use standard shell redirects. so you would do
```
html2text yourinputfile and whatever arguments html2text requires > ~/Desktop/theoutputfile.txt
```
that will automatically take all output from html2text and redirect it to theoutputfile.txt on your desktop. :)

but, html2text is just as good, and probably even better if it aims to preserve some semblance of paragraphs, etc, after stripping out the html.[/QUOTE]

I finally discovered that if I pipe the thing through format to an .rtf file, I can get something readable out of it.

Thanks for the URL

JimW

---

