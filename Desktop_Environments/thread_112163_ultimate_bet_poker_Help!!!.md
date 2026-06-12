---
title: "ultimate bet poker Help!!!"
date: 2006-01-03
forum: Desktop Environments
---

### Post by bfonseca on 2006-01-03
Hi all, I am happy with ubuntu except for one thing and that is I can not get the ultimate bet poker to run.  I have tried all other java based pokers available for linux and am not as happy.  Was kinda hoping someone here has either had this problem already or knows How I can go about fixing this.

I have wine 0.9.3 installed and when I try to run the ubsetup.exe file I get an error 

The error is:

Warning (pop up dialog box)
You need at least Internet Explorer version 4 for install this software

I have looked at other threads online here however have not come up with the solution.  I dont mind having internet explorer installed so I can play this game, but I can not find the internet explorer that is available for linux.

The internet explorer I found for linux is ies4linux, but once installed the setup.exe file for the game doesnt find it or recognize it. I have tried for awhile and have no answer so any help that may lead me in the right direction would be greatly appreciated.

Thanks
Brian

---

### Post by bfonseca on 2006-01-03
So everyone knows I did follow the instructions given by the ies4linux.  Here are the instruction:

Requirements

    * Ok, it is obvious, but we need to say: you need Wine installed!
    * cabextract

Use apt-get, yum, synaptic, emerge etc to install them. Or you can go to their home pages: Wine, cabextract.
Using IEs4Linux

   1. Download IEs4Linux
   2. Open the tar.gz file. You will find a program ies4linux there. Just run it.
   3. You will be asked to choose an installation type. Choose the number, hit enter and go take a nap. If you choose to install all three IEs versions, you have to wait ~250MB to be downloaded. When you come back, everything will be installed for you!
   4. Now, you can type ie6, ie55 or ie5 to open your new IEs!

More options: additionally, you can configure some IEs4Linux options. Do this before running the ies4linux executable. More info here

I installed everything the instructions said to install, I even configured teh config file just like it said and still doesnt work.

Brian

---

### Post by bfonseca on 2006-01-03
Ok I have fixed the internet problem I am now able to run the ,internet explorer 5 ,internet explorer 5.5, and internet explorer 6 on linux and it seems to work fine.  Still the poker software does not work. 1 problem down 1 to go.

---

### Post by Robor on 2006-01-16
I don't have any help to offer but I'll give you a bump since I'm seeking help with Ultimate Bet, Full Tilt, or JetSet Poker.

---

### Post by bfonseca on 2006-01-17
well I got ultimate bet to work, but i did it the hard way. I installed windows xp using vmware and I ran it that what. but I would still like to know how to get it to run on just linux without the immulator. There has got to be an easier way.
Brian

---

### Post by zazuah on 2006-10-26
I was able to get it to work by doing the following:
1.) browse to /home/<owner>/.wine/C_drive/windows
2.) run command 'wine regedit.exe'
3.) in regedit, browse to  '<machine>\HKEY_LOCAL_MACHINE\Software\Microsoft\Internet Explorer'
4.) add the following:
     a. string value named Build with value of 62900.2180
     b. dword value named IntegratedBrowser w value of 1
     c. string value named Version w value of 6.0.2900.2180
     d. string value W2kVersion w value of 6.0.2900.2180
5.) Ran 'wine ubsetup.exe'
6.) Copied over msvcp60.dll from windows machine (c:\windows\system32)

---

