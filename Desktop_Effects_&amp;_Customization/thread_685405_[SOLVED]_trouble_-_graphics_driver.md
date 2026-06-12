---
title: "[SOLVED] trouble - graphics driver"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by lordbux on 2008-02-02
i am having a

**VIA Technologies, Inc. UniChrome Pro IGP (rev 01)**

graphics card 

i went to** [[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220]](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220])**
    VIA Arena  ..as directed by    [https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

but there i got realy confused :confused: :confused: :confused: :confused: :confused:

i got  a long list of drivers
****************************
[B]CLE266 UniChrome integrated graphics
CN700 UniChrome Pro integrated graphics
CN800 UniChrome Pro™ integrated graphics
CN896 VIA Chrome9™ integrated graphics
CX700 UniChrome Pro integrated graphics
CX700M/M2 UniChome Pro integrated graphics
P4M800/CE/Pro UniChrome Pro integrated graphics
P4M890 UniChrome Pro integrated graphics
P4M900 VIA Chrome9™ integrated graphics
PM880, PM800, CN400 UniChrome integrated graphics
PN880 UniChrome Pro integrated graphics
VN800 UniChrome Pro integrated graphics
VN890 UniChrome Pro integrated graphics
VN896 VIA Chrome9™ HC integrated graphics
VX700 Single chip solution
VX700M/M2 Single chip solution[/B]

:(  what to do  [B]SOME ONE SAY WHICH DRIVER OF THE ABOW SHOULD I INSTALL FOR

 THE     **[SIZE="4"] UniChrome Pro IGP (rev 01)[/SIZE]**  GRAPHICS CARD [/B]


PLS HELP

---

### Post by overdrank on 2008-02-02
HI and maybe this link will help
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by lordbux on 2008-02-03
> **overdrank said:**
> HI and maybe this link will help
[B][https://help.ubuntu.com/comChrommunity/Unichrome](https://help.ubuntu.com/comChrommunity/Unichrome)


[B]i had already followd this link  [https://help.ubuntu.com/comChrommunity/Unichrome](https://help.ubuntu.com/comChrommunity/Unichrome) 

and thats when i got the following list of [SIZE="4"]drivers[/SIZE] [/B]

CLE266 UniChrome integrated graphics
CN700 UniChrome Pro integrated graphics
CN800 UniChrome Pro&#8482; integrated graphics
CN896 VIA Chrome9&#8482; integrated graphics
CX700 UniChrome Pro integrated graphics
CX700M/M2 UniChome Pro integrated graphics
P4M800/CE/Pro UniChrome Pro integrated graphics
P4M890 UniChrome Pro integrated graphics
P4M900 VIA Chrome9&#8482; integrated graphics
PM880, PM800, CN400 UniChrome integrated graphics
PN880 UniChrome Pro integrated graphics
VN800 UniChrome Pro integrated graphics
VN890 UniChrome Pro integrated graphics
VN896 VIA Chrome9&#8482; HC integrated graphics
VX700 Single chip solution
VX700M/M2 Single chip solution
[/B]


**but i dont know which one to install for my    [SIZE="4"]UniChrome Pro IGP [COLOR="Red"](rev 01)[/COLOR][/SIZE] GRAPHICS CARD ** 

confused guys        pls help :confused::confused::confused::confused:
pls
help

---

### Post by gobbles414 on 2008-02-03
lordbux,

Can you tell us the model number of your motherboard? For example, I own two VIA motherboards. One of my motherboards is a pc2500 (cn700 chipset), and the other is a pc3500 (cn896 chipset). VIA also makes integrated graphics for other manufactures, I believe. So your motherboard may not be a VIA.

---

### Post by lordbux on 2008-02-03
> **gobbles414 said:**
> lordbux,

Can you tell us the model number of your motherboard? For example, I own two VIA motherboards. One of my motherboards is a pc2500 (cn700 chipset), and the other is a pc3500 (cn896 chipset). VIA also makes integrated graphics for other manufactures, I believe. So your motherboard may not be a VIA.




AM USING AN **AXPER motherboard with VIA chipset-----------i checked it**

is there a way to know the graphisc card ID ...eg  CN700, k800 ............ ect

i dont know the model number
i used the  **'lspci | grep VGA'**   and all it returns is

**[SIZE="4"]VIA Technology's inc : UniChrome Pro IGP (rev 01)[/SIZE]**

how can i het the model number  
pls help 
frnds
:confused: :confused: :confused: :confused:

---

### Post by gobbles414 on 2008-02-03
lordbux,

**How can I get the model number?**
Try pasting _sudo dmidecode | more_ into the terminal.

---

### Post by gobbles414 on 2008-02-03
lordbux,

When you know THE EXACT model number of your motherboard, do a search using Google. For example, Google shows that an *Axper XP-M5VM800* motherboard uses the VIA P4M800 chipset.

---

### Post by gobbles414 on 2008-02-04
lordbux,

I notice that you have marked this issue as solved. Neither of my two VIA motherboards with VIA graphics work correctly in Ubuntu 7.10. Could you please report on how well your graphics are working?

---

### Post by lordbux on 2008-02-07
> **gobbles414 said:**
> lordbux,

I notice that you have marked this issue as solved. Neither of my two VIA motherboards with VIA graphics work correctly in Ubuntu 7.10. Could you please report on how well your graphics are working?

[B]sorry brother for the delay
was away from home thats why[/B] :popcorn:

I JUST INSTALLED THIS DRIVER HERE 
-----------
[http://ubuntuforums.org/attachment.php?attachmentid=53807&d=1198165685](http://ubuntuforums.org/attachment.php?attachmentid=53807&d=1198165685)
**-----------**
[COLOR="Red"]***WARNING AND HELP**[/COLOR]

*1* RUN IT USING .....THE........  **sudo sh [filename]**  COMAND AFTER NAVIGATING TO THE FOLDER
[COLOR="Red"]
*2* WHEN IT ASKS IF IT SHOULD EDIT Xorg.Conf .....**SAY NO**[/COLOR]SAY NO 

THEN CONTINUE  :lolflag: :lolflag:  :guitar:

**_DONOT USE IF USING WIDE SCREEN 19 INCH OR  GREATER _**

---

### Post by gobbles414 on 2008-02-08
lordbux,

I need more information. Please tell me where the attachment comes from. Where did you find that file?

---

### Post by sboutwell on 2008-02-21
> **sauyeeluo said:**
> I recently purchased this board from clubit with 2 gigs of ram.

[B]
Install comments.[/B]
Painless. Everything works out of the box (for the most part).

For video, I used the openchrome driver from the ubuntu repos. After the install I was getting around 200fps give or take 10 percent.  Then ran the following command 'sudo dpkg-reconfigure -phigh xserver-xorg'

selected 'via' as the driver and then the screen resolutions. now, i get about 1000fps running glxgears. i also reduced my bit depth to '16' and i can get approximately 1500fps.  light 3d apps work fine like screensavers. anything graphically intensive will make the board angry. but then again, if your using this board i'd assume your not using it for cad work or gaming.

personally its a great value board.

I followed what this thread listed and openchrome is working 100% for me now.

1. Open Synaptic Package Manager and search for 'openchrome'
2. Install all packages referencing this.  Should be three of them, libviaxvmc1, libviaxvmcpro1, xserver-xorg-video-openchrome.
3. Run the following command     sudo dpkg-reconfigure -phigh xserver-xorg
4. Select via as the driver.
5. System > Administration > Screen and Graphic Preferences.  Select the Graphics card tab and make sure VIA is selected here.
6. Select the screen tab and put in your monitor Model and the Resolution and Hz.
7. Give it a test if you want or Click OK.
8. Log Out and Log back in.  New Resolution and Driver should be enabled.

If not you probably selected an UNSUPPORTED Resolution or Hz for your Monitor or CARD.  BEST TEST before you ACCEPT.

These steps worked for me.  On my PC-1 PC2500 by VIA.  Good Luck.

---

### Post by gobbles414 on 2008-02-21
sboutwell,

I tried the solution that you suggest several weeks ago. 2D acceleration worked fine. But 3D acceleration would not function. Is 3D acceleration working on your system? The only procedure that I have been able to find for getting 3D to work with the CN700 chipset using OpenChrome is located [here]("https://help.ubuntu.com/community/OpenChrome"). Even using those instructions, I haven't been able to get 3D acceleration working in Ubuntu 7.10.

---

### Post by ebeard on 2008-04-03
Thanks Shoutwell.

I have tried all kinds of hints and scripts to get my Unichrome P4M800 working at higher resolution. This finally seems to work (2d at least). VESA limited me to 800x600, now able to max at 1024x768, but that is what I wanted anyway. 

However video stopped working. Changed driver in VLC and got it working. I cannot seem to to get Totem (don't now if I use gtreamer or xine backend) to work. Can't find the configuration file and changing in the dialog box doesn't do it. I am satisfied with VLC, but just for learning experience I would like to know how to configure Totem Movie player. Any hints anyone? What's the path to the file (searched and found one forum article, but I don't have the files it mentioned)?

---

### Post by Xtrmi on 2008-04-05
What is the highest resolution on this chipset in linux. I really want to buy the parts for my green pc but I want 1920 x 1600.

---

