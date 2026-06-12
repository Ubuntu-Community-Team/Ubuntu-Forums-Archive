---
title: "Ubuntu, Eclipse, and Android Development (Buggy?)"
date: 2011-10-04
forum: Desktop Environments
---

### Post by gberar on 2011-10-04
Is it just my particular configuration?  Eclipse seems to be really buggy under Ubuntu 11.04.  Lots of very odd things happen with the IDE. The xml graphical editor seem  to do some very strange re-drawing.

If I edit a file with vim, eclipse gets very unhappy and says I need to refresh.  The refresh doesn't work or is non-existent in the menu. 

Also the thumb bars (horizontal and vertical) are just lines and there is no way to control them.

Is anyone else seeing issues like these?

I am not what you would consider a noob.  This kind of stuff is very frustrating when trying to get something real done.

---

### Post by JHBrewer on 2011-12-27
Not much better under 11.10, apparently: I installed eclipse from synaptic and it looked OK until I tried to look at any of the documentation within eclipse; then (in all cases) I got:   [COLOR=DarkRed][FONT=sans-serif]**HTTP ERROR 500**

Problem accessing /help/index.jsp. Reason:
    The following error occurred while executing this line: XML parser factory has not been configured correctly: Provider org.apache.xerces.jaxp.SAXParserFactoryImpl not found[/FONT]...[/COLOR]

When I Googled this error message I found the following advice (to someone with the same complaint) at **[http://www.eclipse.org/forums/index.php/m/765056/](http://www.eclipse.org/forums/index.php/m/765056/) **:
[I][B]
"Never, never, never get/use and Eclipse from anywhere except eclipse.org 
unless you are on a bizarre platform and have no other choice."[/B][/I]

Is this good advice?  If so, why is eclipse in the repository?  Whom should I trust here?  So far the weight of evidence is on the side of the above advisor, but if I can't trust our own repo, then ... :confused:

I'm not keen to start removing all the files installed by any packages associated with eclipse, but I'm also not keen to start learning this new (to me) IDE without any documentation available.  (Also, if that doesn't work, who knows what else might not?)

---

