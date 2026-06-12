---
title: "Ubutnu 9.04 wLan issues"
date: 2009-05-06
forum: General Help
---

### Post by maxcyber on 2009-05-06
I have done my first install of Linux, ever   
  To get my teenage son up from his basement room I had to provide a laptop so he can IM his friends while being in the same room as his parents  [FONT=Wingdings]:)[/FONT]
  So I found an old Dell Inspiron 5100 with a D-Link AirPlus DWL-650+ card in a cupboard that I had forgotten about
  It was running XP but rather slow, so I thought an Ubutnu install would be cool (I have always wanted to try Linux)
  Everything is working fine except for this tiny issue, it can’t detect our home wLan or any of the neighbours wLan either when running on Ubutnu. When I boot the PC in XP all of them pop’s up. :confused:
  The Question is:
  Do I need to run something special to find the wLan’s?
  Does Ubutnu not detect my D-Link card (it is flashing)?
  Anybody, Please help!
  //Maxcyber

---

### Post by mb_webguy on 2009-05-06
Is that card an internal card or one that plugs in the card slot on the side?

If the former, open the terminal and enter the command "lspci", and look for the card in the list, probably listed as "Network controller".  If it's not listed, then that card is for which drivers haven't been released (or written) for Linux, and you'll have to use the Windows wireless driver with ndiswrapper (which is usually painless).  

You can find the Windows driver on the Dell website, or possibly through the D-Link website.  Once you have it (either by downloading it on another computer or on that one using a network cable) follow [these directions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  If you have problems, here's a [troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847").

---

### Post by maxcyber on 2009-05-13
Below information helped, thanks 

:)

> **mb_webguy said:**
> Is that card an internal card or one that plugs in the card slot on the side?

If the former, open the terminal and enter the command "lspci", and look for the card in the list, probably listed as "Network controller".  If it's not listed, then that card is for which drivers haven't been released (or written) for Linux, and you'll have to use the Windows wireless driver with ndiswrapper (which is usually painless).  

You can find the Windows driver on the Dell website, or possibly through the D-Link website.  Once you have it (either by downloading it on another computer or on that one using a network cable) follow [these directions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").  If you have problems, here's a [troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847").

---

