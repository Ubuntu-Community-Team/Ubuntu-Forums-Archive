---
title: "Toggle between monitors"
date: 2009-11-06
forum: Desktop Environments
---

### Post by Nate0402 on 2009-11-06
I have been looking for a way to toggle between my monitors.  Right now I have a LCD TV and a computer monitor with a nVidia graphics card. I currently go into "nvidia x server settings" and turn one monitor on then turn the other off and then hit apply. I believe that this does not restart X because I don't loose any of my programs. After I am done watching a movie on the LCD TV I turn the computer off and next time I turn the computer on it defaults back to my monitor in the computer room (it does **not** save over my xorg.conf); which I like. 

I would like to know if there is a way to toggle between the monitors with a script or a terminal command. I have tried to look for this every night in the past week with no luck (maybe I am searching with the wrong terms). PLEASE HELP!

---

### Post by m0n0lith on 2011-05-19
I'm resurrecting this ancient thread because it is currently the top Google result for "ubuntu toggle monitors" and I finally found `disper`, a command line tool to do just this.

Webiste: [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

To install via PPA:
sudo add-apt-repository ppa:disper-dev/ppa
sudo apt-get update
sudo apt-get install disper

I used ccsm to configure a keyboard Command shortcut for:

disper --cycle-stages='-s:-S:-c:-e' --cycle

Successive executions of this particular command will toggle the displays between: Primary Monitor Only, Secondary Display Only, Mirrored displays, Extended desktop.  See the man page or disper --help for more options.

I'm running 11.04 on a Dell Latitude E6500 with an nvidia card. Was frustrated to find that Fn+F8 didn't work out-of-the-box but `disper` saves the day!

---

