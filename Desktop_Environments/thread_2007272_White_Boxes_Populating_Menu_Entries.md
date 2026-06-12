---
title: "White Boxes Populating Menu Entries"
date: 2012-06-20
forum: Desktop Environments
---

### Post by lpko908 on 2012-06-20
Good afternoon,

I have does quite a few searches for a solution to this problem, however finding the right phrasing is quite difficult. Hence I turn to the forums. 

To contextualise the problem:

1. I have an eeePC 1000H on which I did a clean install of Ubuntu 12.04. 

2. I installed chromium-browser.

3. I ran ```
sudo apt-get update
```

4. I rebooted.

5. I ran ```
sudo add-apt-repository ppa:ricotz/testing
```

6. I ran ```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

7. I ran ```
sudo apt-get update && sudo apt-get dist-upgrade
```

8. I ran ```
sudo apt-get install gnome-shell gnome-tweak-tool
```

9. I rebooted

_The Problem:_

Upon reaching the login screen, I attempt the select the GNOME desktop environment and the drop-down list is populated with white boxes of different length. Apparently the area that the text occupies is now a white box.

I select what I know to be the GNOME option and log in. Certain menus are having the same problem with the white box behind the text. I check Libre office and find that all the menus have this problem. It appears that not all but most of the menus suffer from this issue. 

In a possibly unrelated issue, I attempt to modify some of the options, for example the screen resolution, and find that I cannot modify the drop down menu. This is the same for the theme choice menu. I can open the menu and see all the options but I cannot change which one is highlighted. 

I hope I have been clear as to the problem. I cannot find a clear solution to this problem. 

I have also checked that the graphics drivers are installed correctly using the command ```
lspci -k
```

and find the driver state to be > 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8340
	Kernel driver in use: i915
	Kernel modules: intelfb, i915


Any help would be much appreciated.

*edit* - grammar

---

### Post by qamelian on 2012-06-20
The problem appears to stem from some items in the ricotz ppa. This issue appeared on my netbook about 2 days ago. ON a hunch last night, I purged the ricotz PPA. That resolved the problem. It only affected me if I was running Unity or was on the lightdm login screen. In Gnome-shell, I didn't experience any issues.
 
Edit: Gnome-tweak-tool had stopped working at the same time. After purging ricotz PPA, it works fine again. Oh, the perils of running along the bleeding edge! :)
 
Edit 2: Before purging the PPA, I also noticed that viewing the display from an extreme angle allowed me to read the nigh-invisble text inside the white boxes.

---

### Post by lpko908 on 2012-06-20
Can you please post the command to purge the ricotz PPA. 

And thank you for the swift reply.

Edit1 - I also noticed that one can see the text at an extreme angle.

Edit2 - Cancel the above request. To be honest I was being a little lazy when I wrote it. Your solution was sound.

For anyone who comes across this thread the solution is as follows:

1. Run ```
sudo apt-get install ppa-purge
```

2. Run ```
sudo ppa-purge ppa:ricotz/testing
```

3. Reboot 

Finished.

Thank you very much *qamelian*.

---

### Post by qamelian on 2012-06-21
No problem. Glad I could help! :)

---

