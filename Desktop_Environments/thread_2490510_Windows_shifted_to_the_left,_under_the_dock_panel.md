---
title: "Windows shifted to the left, under the dock panel"
date: 2023-09-06
forum: Desktop Environments
---

### Post by georgesgiralt on 2023-09-06
Hello Guys, 
On my laptops (both Lenovo, with Nvidia Optimus graphics and Intel embedded graphics cards, one laptop 10 years old the other one more modern) I run Nvidia 535 proprietary drivers.
I have always a lot of windows open (Firefox, Thunderbird, Gpodder, and so on...).
Often, when I want to work on a window, whatever it is, the left side of the window is masked (see the picture). 
[IMG]https://i19.servimg.com/u/f19/17/79/70/72/captur41.png[/IMG]
I can't find what's wrong. 
So I would be delighted to get some help. 
Many thanks in advance for your help.
Have a nice day !

---

### Post by ActionParsnip on 2023-09-06
Have you set the dock to autohide?

This may help:
[https://askubuntu.com/questions/1053543/how-do-i-show-ubuntu-dock-always-over-maximized-windows-without-the-need-for-au](https://askubuntu.com/questions/1053543/how-do-i-show-ubuntu-dock-always-over-maximized-windows-without-the-need-for-au)

---

### Post by georgesgiralt on 2023-09-06
Hello 
Thank you for your help
No I did not. The dock is fixed and steady....
I'll read your link later.

---

### Post by georgesgiralt on 2023-09-07
Hello, 
Here am I again. 
Actually, this behaviour is new. Both laptop ran Ubuntu since a long time for the oldest and was running 20.04 for the newest. This was not existent on previous versions of Ubuntu. 
The older laptop evolved from many versions of Ubuntu Linux during "the ages" and the new got reinstalled in 22.04 because I wanted a clean install after a busy life under 20.04....
As the hardware did not change, I wonder if the culprit is the Nvidia driver (I installed the "tested" version to err on the safe side or the newer Linux Kernel compared to the one delivered with 20.04.
I read your post linked above and did not find it too useful (I'm very busy these days because of deadlines I've to meet and can't experiment a lot)
Anyway, thank you for your help.

---

### Post by mIk3_08 on 2023-09-09
Best solution for this matter is to auto hide the dock panel of your Ubuntu Desktop Environment so that, when you decide to maximize the window you use it will not distract you anymore when the dock panel overlaps the window you maximize.

To auto-hide the dock panel, you can follow these steps:

Open the Settings app.
Click on the Appearance tab.
Under the Dock section, check the box next to "Auto-hide the dock".
Click on the Apply button.
Once you have enabled the auto-hide feature, the dock panel will disappear when you are not using it. It will only reappear when you move your mouse cursor to the bottom of the screen.

This is a great way to free up screen space when you are working on a maximized window. It also prevents the dock panel from overlapping with the window you are maximizing.

Here are some additional things to keep in mind:

You can also adjust the sensitivity of the auto-hide feature. This will determine how close you need to move your mouse cursor to the bottom of the screen before the dock panel reappears.
You can also choose to have the dock panel always visible on the left or right side of the screen.
If you have a lot of icons on your dock panel, you may want to consider using a different layout. This will help to prevent the dock panel from becoming too cluttered.

Regards and cheers

---

### Post by georgesgiralt on 2023-09-09
Thank you for your answer and tips, but I do not understand.
I use GNU/Linux systems since kernel 1.1. So I've encountered many many desktop environments. 
These two laptops were running previous version of Ubuntu. And as I'm an old man, I restore my settings the same every time I open a new session. 
All my windows, be them apps or terminal, are maximised because I do not want to loose any space on my screens. 
It is the first time I see this behaviour, so IMHO this is a bug. Never, ever did the dock overlapped any windows before. Of course, as the Gnome subsystem version is not the same than the one used previously and as the Nvidia drivers are also different, I can't tell where the bug lies, but, either it is a default configuration error (from Ubuntu or Gnome teams, as I use the defaults as shipped) or a bug.... 
Masking the dock will force me to learn new way to work. 
I bet I'm too old for that. 
Have a nice and bright day.

---

### Post by mIk3_08 on 2023-09-09
I understand you and I am very sorry for that. I know its very annoying.
Did you try to switch to xorg? I think think I don't have same problem as yours. Im using xorg right now.
see image below:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292706&stc=1[/IMG]
or you can use different dock extensions if you want..
Regards and cheers

---

### Post by atta726 on 2023-09-10
[COLOR=#374151][FONT=Söhne]The issue you're experiencing with window masking on your Lenovo laptops running Nvidia drivers might be related to screen resolution or graphics card settings. Here are some steps to troubleshoot and resolve the problem:[/FONT][/COLOR]

[LIST=1]
[*] Ensure your screen resolution is set correctly. Right-click on the desktop, go to Display Settings (or Screen Resolution), and choose a resolution that matches your laptop's screen.
[*]Make sure your Nvidia graphics drivers are up to date. Visit the Nvidia website or use the Nvidia GeForce Experience application to check for and install the latest drivers.
[*] In Nvidia Control Panel, navigate to "Display" and adjust the scaling settings. Try setting it to "No Scaling" or "Aspect Ratio" to prevent any window masking due to improper scaling.
[*] Sometimes, multiple windows can overlap, causing parts of one window to be hidden. Use the Windows key + Tab to view all open windows and make sure they are arranged correctly.
[*]Some third-party applications, especially those related to graphics or screen management, can interfere with window positioning. Try disabling or uninstalling such applications temporarily to see if the issue persists.
[*]If your laptops have both Nvidia and Intel graphics, try switching between them (if supported) to see if the problem occurs with one graphics card but not the other. This can help pinpoint the issue.
[*]Ensure your operating system and all related software are up to date. Sometimes, updates can resolve compatibility issues.
[*]High GPU temperatures can sometimes lead to display issues. Use software like MSI Afterburner or GPU-Z to monitor your GPU's temperature and ensure it's within a safe range.
[*] In some applications like web browsers, hardware acceleration can cause graphical glitches. Try disabling it in the settings of the affected applications.
[*] If none of the above solutions work, consider resetting your graphics card settings to their default values in the Nvidia Control Panel.
[/LIST]
[COLOR=#374151][FONT=Söhne]If the problem persists after trying these steps, it might be helpful to provide more details about your specific Nvidia graphics card model and the operating system version you're using. Additionally, check if the issue occurs on an external monitor or only on your laptop's screen, as this can provide further insights into the problem's cause[/FONT][/COLOR]

---

### Post by georgesgiralt on 2023-09-10
Thank you, atta726 for your answer. 
Below are my responses to your step by step instructions.

> **atta726 said:**
> [COLOR=#374151][FONT=Söhne]The issue you're experiencing with window masking on your Lenovo laptops running Nvidia drivers might be related to screen resolution or graphics card settings. Here are some steps to troubleshoot and resolve the problem:[/FONT][/COLOR]

[LIST=1]
[*] Ensure your screen resolution is set correctly. Right-click on the desktop, go to Display Settings (or Screen Resolution), and choose a resolution that matches your laptop's screen.
Resolution are set to the native laptop screen. 1920*1080.

> [*]Make sure your Nvidia graphics drivers are up to date. Visit the Nvidia website or use the Nvidia GeForce Experience application to check for and install the latest drivers.
I use the additional driver app to install the drivers as I _do_ prefer the one Canonical ship above the NVidia one (I had many very bad experiences using them in the past...).
Both machines use the "nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic-hwe-22.04)" as it is said "tested".

> [*] In Nvidia Control Panel, navigate to "Display" and adjust the scaling settings. Try setting it to "No Scaling" or "Aspect Ratio" to prevent any window masking due to improper scaling.
No such settings see image : 
[IMG]https://i19.servimg.com/u/f19/17/79/70/72/nvidia10.png[/IMG]
> [*] Sometimes, multiple windows can overlap, causing parts of one window to be hidden. Use the Windows key + Tab to view all open windows and make sure they are arranged correctly.
I have one window/one app per working space. So "normally" no overlapping.
> [*]Some third-party applications, especially those related to graphics or screen management, can interfere with window positioning. Try disabling or uninstalling such applications temporarily to see if the issue persists.
No such thing what I know of...  But I can't vouch for all apps Canonical install without me knowing. 
> [*]If your laptops have both Nvidia and Intel graphics, try switching between them (if supported) to see if the problem occurs with one graphics card but not the other. This can help pinpoint the issue.
My Optimus settings are set to "On Demand" as I use sometimes the laptop on it's battery and do not need extra power graphics that often.
> [*]Ensure your operating system and all related software are up to date. Sometimes, updates can resolve compatibility issues.
Always do. 40 years in IT specializing in big servers and security leaves traces and habits.
> [*]High GPU temperatures can sometimes lead to display issues. Use software like MSI Afterburner or GPU-Z to monitor your GPU's temperature and ensure it's within a safe range.
As you can see on the picture attached above, you will see that the temperature is in the safe zone.
> [*] In some applications like web browsers, hardware acceleration can cause graphical glitches. Try disabling it in the settings of the affected applications.
Strangely, the navigators are never impacted. The usual suspects are terminal app, Gpodder,and Thunderbird.
> [*] If none of the above solutions work, consider resetting your graphics card settings to their default values in the Nvidia Control Panel. 
No such option in the app I have. 
> [/LIST]
[COLOR=#374151][FONT=Söhne]If the problem persists after trying these steps, it might be helpful to provide more details about your specific Nvidia graphics card model and the operating system version you're using. Additionally, check if the issue occurs on an external monitor or only on your laptop's screen, as this can provide further insights into the problem's cause[/FONT][/COLOR]
The laptop I use for posting this has 
NVIDIA GeForce MX450 with 90.17.64.00.14 VBios. 
I run kernel 6.2.0-32-generic #32~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC 
and nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic-hwe-22.04).
Processor is : 11th Gen Intel® Core™ i5-1135G7 @ 2.40GHz × 8
And I use Ubuntu 22.04.3 LTS .
Alas I do not have any external monitor. And using the TV set is very difficult, as I can't reach the HDMI plugs (the TV is affixed to the wall).
Again, thanks for your help

---

### Post by sideaway on 2023-09-14
Interestingly, I get the same bug - happens quite often after the laptop has slept.

AMD Ryzen 7 5800u
AMD Radeon RX Vega 8
Kernel 6.2.0-32-generic
amdgpu 2.4.113-2
Ubuntu 22.04.3
I often run multi monitor - but doesn't seem to be necessary for the bug to occur.

---

### Post by ytxmobile on 2024-07-22
> **georgesgiralt said:**
> Hello, 
Here am I again. 
Actually, this behaviour is new. Both laptop ran Ubuntu since a long time for the oldest and was running 20.04 for the newest. This was not existent on previous versions of Ubuntu. 
The older laptop evolved from many versions of Ubuntu Linux during "the ages" and the new got reinstalled in 22.04 because I wanted a clean install after a busy life under 20.04....
As the hardware did not change, I wonder if the culprit is the Nvidia driver (I installed the "tested" version to err on the safe side or the newer Linux Kernel compared to the one delivered with 20.04.
I read your post linked above and did not find it too useful (I'm very busy these days because of deadlines I've to meet and can't experiment a lot)
Anyway, thank you for your help.

Definitely not related to NVIDIA. My laptop uses Intel integrated graphics card and this problem also exists here.

---

