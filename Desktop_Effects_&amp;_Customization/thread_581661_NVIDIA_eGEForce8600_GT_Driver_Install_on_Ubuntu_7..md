---
title: "NVIDIA eGEForce8600 GT Driver Install on Ubuntu 7.10"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by harsh2209 on 2007-10-19
Newly installed Ubuntu 7.10 Desktop edition.
Wanted to install Nvidia 2-GeForce 8600 GT Drivers.
Downloaded driver from: [http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html)
Solution that worked out for me.
1. Log-in as normal user.
2. Then go to Terminal and type &#8216;apt-get install build-essential&#8217;.
3. Wait until it returns the prompt and no errors displayed.
4. Then press (without quotes) &#8216;Ctrl+Alt+F1&#8217;.
5. Screen will flicker and you will see command line.
6. Log-in as root.
7. Stop X-Server by &#8216;sudo /etc/init.d/gdm stop&#8217;.
8. Now cd to the location where the Nvidia driver is.
9. And run it as &#8216;sh driver-name&#8217;
10. It will ask to accept. Accept it.
11. Then it will say that no precompiled kernel found etc. and would you like it to download from &#8216;ftp&#8230;&#8217;
12. Say yes&#8230; and it should successfully begin the installation.
13. When finished type on the prompt &#8216;sudo /etc/init.d/gdm restart&#8217;.
14. For a moment you should see nvidia logo. It means you are successful.
------------------------------------------------

However, when I clcik restart the system it hangs on the black  console screen. When I hard shutdown the m/c  and restart it, I get ubuntu is in low graphics mode. I get Resolution and Graphics card  option to manually select and test. It boots up but then, from the Admin -> Restricted drivers -> NVIDIA is disabled. When I try to enable it says 'nvidia-glx-new' disabled ... Any help....

---

