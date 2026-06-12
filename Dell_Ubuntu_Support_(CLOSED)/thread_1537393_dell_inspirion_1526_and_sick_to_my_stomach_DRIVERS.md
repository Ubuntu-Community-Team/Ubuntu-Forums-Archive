---
title: "dell inspirion 1526 and sick to my stomach DRIVERS!!!!!"
date: 2010-07-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dirkyboy on 2010-07-23
I was having good vibes upon making my dell a dual boot.. Loved kubuntu GUI but the drivers are a nightmare. OK, The stock wireless card wouldnt work with Kibuntu network manager. I tried the whole ndiswrapper thing with no success. I gave up and finally I saw this card and purchased it thinking it would make my life easier.
 
[http://www.dealextreme.com/details.dx/sku.35897](http://www.dealextreme.com/details.dx/sku.35897)
 
The forums post on this had this below so I thought installation would be a breeze. I dont know what I'm doing wrong. I went to realtek where they said and downloaded the driver. I have extracted to the DRIVER folder under home, cd'd to that directory and did a MAKE. I keep getting errors on that driver something about interger.. I then found the CD that came with the card and copied the driver directory from the CD to the DRIVER folder under home. I'm logged in as root. I did a make but still getting errors and nothing showing up under IWCONFIG. I rebooted and when I do, If i reboot with wireless card inserted into USB slot, the CAPS lock and NUM lock lights next to the power button are blinking and I get a black screen. If I reboot with no USB wireless card installed in the USB slot, It will go into Kubuntu..
 
HELLLPPP!!!! I'm getting extremely frustrated and at my wits end with this linux! I almost hate the fact its not plug and play like windows.. GIVE me a reason to keep this stuff on my HD!;)
----------------------------------------------------------- so --------
[FONT=Verdana]Subject: **Ubuntu/Linux support**[/FONT] 
 
1[2]("http://javascript<b></b>:__doPostBack('threadView','Page$2')")[FONT=Verdana][SIZE=2][COLOR=navy]**frankynov **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Monday, June 21, 2010 8:07 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Hello everybody ! [/FONT]
 
[FONT=Verdana]I'm very interested in this chipset for a friend running Ubuntu 10.04. [/FONT]
[FONT=Verdana]Has anyone tested it on a linux distribution ? What are the results ? I'd like to have a 'real' go/no go instead of the commercial and generic message on the packaging  [/FONT]
 
[FONT=Verdana]Thank you ! [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.frankynov") (4) | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.frankynov") (0) | [Tip Post]("http://javascript<b></b>:TipPost(642605, 'frankynov');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.642605") []("http://javascript<b></b>:ReportPost(642605);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**Morvan **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Tuesday, June 22, 2010 7:14 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Hi, **frankynov**. I downloaded and compiled this driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU) directly from Realtek. It worked no any problem on **Ubuntu 10.04 and Fedora 13 (both 32bits; on Fedora 13x64, which I have in other partition, I could not put it to work)**. You can download from Realtek, it is more secure to work then this driver brought on the CD. [/FONT]
[FONT=Verdana]You will have to do is simply command "make; make install" and connect device... [/FONT]
 
[FONT=Verdana]Regards, [/FONT]
 
[FONT=Verdana]Morvan, User Linux #433640 [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.Morvan") ( | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.Morvan") (6) | [Tip Post]("http://javascript<b></b>:TipPost(643875, 'Morvan');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.643875") []("http://javascript<b></b>:ReportPost(643875);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**frankynov **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Wednesday, June 23, 2010 7:55 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Thanks a lot Morvan ! [/FONT]
[FONT=Verdana]I don't care about compiling.. In fact I love when things don't work at first, it makes me learn more stuff about linux ! [/FONT]
 
[FONT=Verdana]I'll give it a try !  [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.frankynov") (4) | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.frankynov") (0) | [Tip Post]("http://javascript<b></b>:TipPost(644231, 'frankynov');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.644231") []("http://javascript<b></b>:ReportPost(644231);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**TheLazza **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Wednesday, June 23, 2010 11:40 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Also remember you could always use NdisWrapper as a last chance. [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.TheLazza") ( | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.TheLazza") (3) | [Tip Post]("http://javascript<b></b>:TipPost(644415, 'TheLazza');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.644415") []("http://javascript<b></b>:ReportPost(644415);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**MolaMolard **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Friday, June 25, 2010 1:55 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]HI, [/FONT]
[FONT=Verdana]Does this mean you can actually use packet injection [using air.crack and stuff] ? [/FONT]
 
 
[FONT=Verdana]thx guys [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.MolaMolard") (1) | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.MolaMolard") (0) | [Tip Post]("http://javascript<b></b>:TipPost(646029, 'MolaMolard');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.646029") []("http://javascript<b></b>:ReportPost(646029);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**Vladlenin **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Friday, June 25, 2010 2:24 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Yes, it does. Have fun  [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.Vladlenin") (283 | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.Vladlenin") (13) | [Tip Post]("http://javascript<b></b>:TipPost(646044, 'Vladlenin');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.646044") []("http://javascript<b></b>:ReportPost(646044);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**TheLazza **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Saturday, June 26, 2010 3:49 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]What about Access Point mode? My Intel card doesn't work as an Access Point under Linux.  [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.TheLazza") ( | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.TheLazza") (3) | [Tip Post]("http://javascript<b></b>:TipPost(646351, 'TheLazza');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.646351") []("http://javascript<b></b>:ReportPost(646351);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**jose1711 **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Friday, July 02, 2010 1:05 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]i confirm it works flawlessly on arch linux. the only thing i had to do was put firmware rtl8192sfw.bin into /lib/firmware/RTL8192SU. module in use is r8192s_usb [/FONT]
[FONT=Verdana]lsusb: [/FONT]
[FONT=Verdana]Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. [/FONT]
 
[FONT=Verdana]the device is stable, but better plug it directly into usb (had problems when connected via pcmcia usb hub). it also gets a bit warm but it's no big deal. [/FONT]

---

### Post by tkoco on 2010-07-24
Wireless support can be a bit shakey. It is a good idea to ask here on the forums first before spending your money. From your message, it sounds like the USB device can be made to work, but the level of expertise is bit higher than normal. I have used the following USB wireless straight from the box on Jaunty, Karmic, and current Lynx releases:

[http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=linksys+USB&oe=utf-8&um=1&ie=UTF-8&cid=6706243103814026128&ei=pH1LTK-bF8L78AawnaUy&sa=X&oi=product_catalog_result&ct=result&resnum=5&ved=0CFAQ8wIwBA#]("http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=linksys+USB&oe=utf-8&um=1&ie=UTF-8&cid=6706243103814026128&ei=pH1LTK-bF8L78AawnaUy&sa=X&oi=product_catalog_result&ct=result&resnum=5&ved=0CFAQ8wIwBA#")

It is not as compact as the dongle USB which you reference, but it does work. I would like to warn you that I had the USB device plugged in while I loaded Ubuntu from scratch. That way the installation program would find it and load up the necessary software to make it work.


> **dirkyboy said:**
> I was having good vibes upon making my dell a dual boot.. Loved kubuntu GUI but the drivers are a nightmare. OK, The stock wireless card wouldnt work with Kibuntu network manager. I tried the whole ndiswrapper thing with no success. I gave up and finally I saw this card and purchased it thinking it would make my life easier.
 
[http://www.dealextreme.com/details.dx/sku.35897](http://www.dealextreme.com/details.dx/sku.35897)
 
The forums post on this had this below so I thought installation would be a breeze. I dont know what I'm doing wrong. I went to realtek where they said and downloaded the driver. I have extracted to the DRIVER folder under home, cd'd to that directory and did a MAKE. I keep getting errors on that driver something about interger.. I then found the CD that came with the card and copied the driver directory from the CD to the DRIVER folder under home. I'm logged in as root. I did a make but still getting errors and nothing showing up under IWCONFIG. I rebooted and when I do, If i reboot with wireless card inserted into USB slot, the CAPS lock and NUM lock lights next to the power button are blinking and I get a black screen. If I reboot with no USB wireless card installed in the USB slot, It will go into Kubuntu..
 
HELLLPPP!!!! I'm getting extremely frustrated and at my wits end with this linux! I almost hate the fact its not plug and play like windows.. GIVE me a reason to keep this stuff on my HD!;)
----------------------------------------------------------- so --------
[FONT=Verdana]Subject: **Ubuntu/Linux support**[/FONT] 
 
1[2]("http://javascript<b></b>:__doPostBack('threadView','Page$2')")[FONT=Verdana][SIZE=2][COLOR=navy]**frankynov **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Monday, June 21, 2010 8:07 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Hello everybody ! [/FONT]
 
[FONT=Verdana]I'm very interested in this chipset for a friend running Ubuntu 10.04. [/FONT]
[FONT=Verdana]Has anyone tested it on a linux distribution ? What are the results ? I'd like to have a 'real' go/no go instead of the commercial and generic message on the packaging  [/FONT]
 
[FONT=Verdana]Thank you ! [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.frankynov") (4) | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.frankynov") (0) | [Tip Post]("http://javascript<b></b>:TipPost(642605, 'frankynov');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.642605") []("http://javascript<b></b>:ReportPost(642605);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**Morvan **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Tuesday, June 22, 2010 7:14 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Hi, **frankynov**. I downloaded and compiled this driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188SU) directly from Realtek. It worked no any problem on **Ubuntu 10.04 and Fedora 13 (both 32bits; on Fedora 13x64, which I have in other partition, I could not put it to work)**. You can download from Realtek, it is more secure to work then this driver brought on the CD. [/FONT]
[FONT=Verdana]You will have to do is simply command "make; make install" and connect device... [/FONT]
 
[FONT=Verdana]Regards, [/FONT]
 
[FONT=Verdana]Morvan, User Linux #433640 [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.Morvan") ( | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.Morvan") (6) | [Tip Post]("http://javascript<b></b>:TipPost(643875, 'Morvan');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.643875") []("http://javascript<b></b>:ReportPost(643875);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**frankynov **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Wednesday, June 23, 2010 7:55 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Thanks a lot Morvan ! [/FONT]
[FONT=Verdana]I don't care about compiling.. In fact I love when things don't work at first, it makes me learn more stuff about linux ! [/FONT]
 
[FONT=Verdana]I'll give it a try !  [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.frankynov") (4) | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.frankynov") (0) | [Tip Post]("http://javascript<b></b>:TipPost(644231, 'frankynov');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.644231") []("http://javascript<b></b>:ReportPost(644231);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**TheLazza **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Wednesday, June 23, 2010 11:40 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Also remember you could always use NdisWrapper as a last chance. [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.TheLazza") ( | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.TheLazza") (3) | [Tip Post]("http://javascript<b></b>:TipPost(644415, 'TheLazza');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.644415") []("http://javascript<b></b>:ReportPost(644415);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**MolaMolard **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Friday, June 25, 2010 1:55 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]HI, [/FONT]
[FONT=Verdana]Does this mean you can actually use packet injection [using air.crack and stuff] ? [/FONT]
 
 
[FONT=Verdana]thx guys [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.MolaMolard") (1) | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.MolaMolard") (0) | [Tip Post]("http://javascript<b></b>:TipPost(646029, 'MolaMolard');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.646029") []("http://javascript<b></b>:ReportPost(646029);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**Vladlenin **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Friday, June 25, 2010 2:24 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]Yes, it does. Have fun  [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.Vladlenin") (283 | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.Vladlenin") (13) | [Tip Post]("http://javascript<b></b>:TipPost(646044, 'Vladlenin');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.646044") []("http://javascript<b></b>:ReportPost(646044);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**TheLazza **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Saturday, June 26, 2010 3:49 AM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]What about Access Point mode? My Intel card doesn't work as an Access Point under Linux.  [/FONT]
 
[FONT=Verdana][IMG]http://www.dealextreme.com/images/spacer.gif[/IMG] [COLOR=#6c6c6c][Posts]("http://www.dealextreme.com/forums/forums.dx/op.TheLazza") ( | [Reviews]("http://www.dealextreme.com/feedbacks/browsereviews.dx/op.TheLazza") (3) | [Tip Post]("http://javascript<b></b>:TipPost(646351, 'TheLazza');") [/COLOR][/FONT]
[FONT=Verdana][]("http://www.dealextreme.com/Forums/EditPost.dx/PostID.646351") []("http://javascript<b></b>:ReportPost(646351);") [/FONT]
[FONT=Verdana][SIZE=2][COLOR=navy]**jose1711 **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]Friday, July 02, 2010 1:05 PM [/SIZE][/FONT][FONT=Verdana][SIZE=2][Reply]("http://www.dealextreme.com/forums/Default.dx/sku.35897~threadid.642605#compose") [/SIZE][/FONT][FONT=Verdana]i confirm it works flawlessly on arch linux. the only thing i had to do was put firmware rtl8192sfw.bin into /lib/firmware/RTL8192SU. module in use is r8192s_usb [/FONT]
[FONT=Verdana]lsusb: [/FONT]
[FONT=Verdana]Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. [/FONT]
 
[FONT=Verdana]the device is stable, but better plug it directly into usb (had problems when connected via pcmcia usb hub). it also gets a bit warm but it's no big deal. [/FONT]

---

### Post by dirkyboy on 2010-07-25
i was FINALLY able to get the dell native wireless card working by finding the "DRIVERS'' link in the GUI menu.. clicked on it and WALLA! I am tooo po'd though for words having spent countless hours in the command line.

---

### Post by texaswriter on 2010-07-26
dirkyboy> Yeah, something I used to do [back when I used kubuntu], is search for kde or kubuntu *plus* whatever I was searching for... Sometimes things work differently in kde... You definitely have different utilities and applications for a lot of things. Why KDE and Kubuntu decided to implement their own version of *some* things when they don't work well is beyond me. 

Anyways, glad you got your driver working. And just remember: google is your friend: 

inurl:ubuntuforums.org kubuntu wireless  xyz

---

