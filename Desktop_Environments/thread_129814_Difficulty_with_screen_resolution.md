---
title: "Difficulty with screen resolution"
date: 2006-02-14
forum: Desktop Environments
---

### Post by Bluztrvler on 2006-02-14
Been trying all day to find a way to adjust  my screen resolution to 1024 X 768, but no matter what I try, nothing seems to make any difference. I have an older nvidia gforce card which works well with windows. I loaded different nvidia drivers, modified my etc/X11/xorg.conf settings, and made adjustments with the system configuration editor (it allowed me the change the numbers to 1024 X768, but the screen rez did not change.  The screen resolution settings on the System ..Preference drop down boxes list only 640X480 and 600X800, and haven't changed regardless of what other changes I make.  

Greatful for any guidance.

---

### Post by taurus on 2006-02-14
Try changing it in /etc/X11/xorg.conf with a text editor.  If you scroll down toward the bottom of that files, you we will a section where it lists all the resolutions so just add whichever one you want to use infront of it.  Then, either restart your X or reboot.

---

### Post by RAOF on 2006-02-14
There's a link to the ultimate guide to Xorg resolution problems on the second row of my sig.  Try that?

---

### Post by Bluztrvler on 2006-02-14
Taurus,

Thanks, that is what I did. I used a terminal window to eidt it. When I checked the file later, my changes were there, but still only 800X600.

---

### Post by taurus on 2006-02-14
Did you remember to restart X or reboot after you've made the change???

---

### Post by Bluztrvler on 2006-02-15
To Taurus,

Yes, I rebooted.

To anyone

I ran the reconfigure routine and I think I see the problem. When it comes to setting the screen resolution, it says to REMOVE any entries that you do not want your screen to display. 1024X768 is not checked on that list and I could find no way to check it. 

My feeling is that the configuration file for my particlar video card (Nvidia 256DDR) thinks that my card is not capable of screen rez higher than 800X600.

Does anyone know of a way that I can check the 1024X768 entry in the Xorg reconfiguration file,  or how I can change the  video card config file, or another way arround this?

Thanks

---

### Post by frodon on 2006-02-15
BluztrvIer, in most of the case you need to put the horizontal and vertical refresh rates of your screen in the xorg.conf file to enable higher resolutions and all is explained in the guide that RAOF gave you : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

good luck ;)

---

### Post by missmoondog on 2006-02-15
here's the thread that cured my exact same problem.

[http://www.ubuntuforums.org/showthread.php?t=109258](http://www.ubuntuforums.org/showthread.php?t=109258)

---

### Post by Bluztrvler on 2006-02-15
Thanks to all,

Obviously, I am a newb to this Ubuntu world. If we were working in DOS, I would be right at home. I have a LCD monitor from Ashton Digital, and they are out of business. I have  no idea what settings I need to use to make it work. I suppose I will just experiment. The suggestions by RAOF look very helpful, and I had tried some of his suggestions earlier. My last attempt shut the GUI down completely, so I guess I am making progress. 

Bluztrlver

---

### Post by Bluztrvler on 2006-02-15
I tried the suggestions that frodon and missmoondog suggested and indeed I was able to increase my refresh rate, but in my particular case 60hz is good. Still I wasn't able to access the 1024X768 rez that I had added to my xorg.conf file. When I installed my system, the default monitor was selected for me. Could there be another setting that is causing it not to work. 

To RAOF 
What is modelline? It looks like it changes the Hor and Ver Frequences (refresh rate) but the code it creates looks like nothing else in my xorg.conf file.
When I added the code, the GUI wouldn't start. I used 1024X768 at 60hz to create it.

Bluztrvler

---

### Post by Bluztrvler on 2006-02-15
Still no luck,

I ran the horizontal and vertical refresh rates up until the monitor stopped working. LCD monitors of this generation at least are very happy with this setting at 60hz, but I was able to get it to 85hz. So it looks like something is happening when I make changes in my xorg.conf file. I add 1024X768 successfully to the list of usable screen resolutions, but they are not accessable to me after the GUI starts. When I run the reconfiguration program, it sees my monitor as a default monitor and I haven't found a way to change that.

So, if there are any other ideas, I would be greatful. 

Bluztrvler

---

### Post by Bluztrvler on 2006-02-16
Thanks to all for their help. I finally found the answer. When I typed 1024X768 in my xorg.conf file I used an Upper Case X between 1024 and 768 instead of a lower case x. When I changed this, 1024x768 was available.

Thanks again,
Bluztrvler

---

