---
title: "how to install modem in LATITUDE D600"
date: 2007-12-02
forum: Dell  Ubuntu Support
---

### Post by rightman2928 on 2007-12-02
Hello Every one...

I have Installed Ubuntu 7.4 on dell Lattitude D600...plz tell me how to Install Modem.....:confused:i want to use dailup on Ubountu

Regards 

Mani

---

### Post by kgr132 on 2007-12-20
I have a D600 and I used the driver provided by Dell for the Inspiron E1505n, 1420n. Apparently they use a similar Conexant HSF software modem. The Inspiron driver even listed my modem as a compatible model and it's working just fine. The Dell provided driver appears to be an OEM licensed version of the package sold by Linuxant. You can get the latest version from Dell here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

The only odd thing I noticed is that the modem device linked to ttySHSF0 and the config tool isn't obvious (type: sudo hsfconfig in a terminal). Although I didn't have any trouble with the driver, there's also a Dell Community support thread on it here:
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10843&view=by_date_ascending&page=1](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=10843&view=by_date_ascending&page=1)

Good Luck.

edit: I just noticed that you said you're using Ubuntu 7.04. A link for a driver for that version is here:
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

---

### Post by vavoem on 2008-01-01
:KS Thanx i confirm this to be a working solution on my dell d600 lappie.
Running 7.04 
wget [http://ftp.us.dell.com/comm/hsfmodem_7.60.00.06oem_i386.deb](http://ftp.us.dell.com/comm/hsfmodem_7.60.00.06oem_i386.deb)
sudo dpkg -i hsfmodem_7.60.00.06oem_i386.deb
answer the questions and your done.

---

