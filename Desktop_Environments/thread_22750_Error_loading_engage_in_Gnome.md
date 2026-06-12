---
title: "Error loading engage in Gnome"
date: 2005-03-29
forum: Desktop Environments
---

### Post by bodyhead on 2005-03-29
Guys, I'm trying to get engage working.  I've managed to download the e17 packaged versions from a mirror off [http://shadoi.soulmachine.net](http://shadoi.soulmachine.net) .   I installed enlightenment enlightenment-data eutils engage.  When I try to load engage, I should get a rectange with question marks going across the bottom of the screen but instead I get a long grey flickering rectangle which destroys my system responsiveness.

Below are several screenshots.  
Sometimes engage kind of loads up but sometimes it doesn't.

[http://www.cbu.edu/~jpmyers/Screenshot.png](http://www.cbu.edu/~jpmyers/Screenshot.png)
[http://www.cbu.edu/~jpmyers/Screenshot-1.png](http://www.cbu.edu/~jpmyers/Screenshot-1.png) 
[http://www.cbu.edu/~jpmyers/Screenshot-2.png](http://www.cbu.edu/~jpmyers/Screenshot-2.png)

Can anyone give any instructions or help?

EDIT:
I actually got it to give me the default format.  I think that for whatever reason, engage didn't like my particular resolution.  I installed my actual ati driver and switched my resolution and now I see the question marks like I am suppose to.

Thanks anyway fellas.

EDIT:  
I have uninstalled the engage taskbar because it still seems very buggy to me.  I have tried to use it on seperate computers.  Each time I came up with sub-par results.  I will just wait for a beta release of the package.

---

### Post by Cimmerian on 2005-04-03
I'm not sure how well you got it working, so I thought I'd mention that I'm running engage "perfectly" here using the same packages. IIRC it behaved like you describe until I configured it correctly. By that I mean creating the .eapp files in ~/.e/e/applications/all and populating it in the file ~/.e/e/applications/engage/.order. The .eapp files were created with [e17genmenu](http://www.sourceforge.net/projects/e17genmenu) (which had to be hacked a little to get working). 

By "perfectly" I mean I am only using it as a launcher with a clock as it really didn't work well as a real dock (minimization/maximization etc). Some applications would work as they should, while others would not.

This is how it looks: 

[[IMG]http://www.pvv.org/~jorgensa/ss/engage_small.png[/IMG]](http://www.pvv.org/~jorgensa/ss/engage_full.png)

Themes are easily selectable using command line or the configuration gui.

---

### Post by bodyhead on 2005-04-11
Well your dock does look pretty nice but I still think I'll wait until it is a little more polished.  I would like to have a Linux setup that is close enough to Mac OS X to fool users.  I don't think the engage dockbar will give me that capability yet.

---

