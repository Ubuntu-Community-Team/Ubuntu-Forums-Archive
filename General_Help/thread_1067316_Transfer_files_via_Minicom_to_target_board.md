---
title: "Transfer files via Minicom to target board"
date: 2009-02-11
forum: General Help
---

### Post by hurdy on 2009-02-11
Hi everynone,

Firstly, may I thank you for takimg the time to read this.

I'm having trouble transfering a binary file to my destination board via the minicom. My destination board is a Beagleboard [www.beagleboard.org](www.beagleboard.org) using one of the latest embedded linux kernals.

I have the minicom setup correctly so I can control my target board via minicom.

Now, according to the minicom manual, when running minicom I can enter a menu by press CTRL-A Z. This works fine. I select the option for File Transfer and it brings up a list of ymodem, xmodem, zmodem, kermit and ascii.

I selet one of the following (not really sure which is the correct one to choose) and it brings up a list of files located on my host machine. I selected the file I want to transfer using the SPACE key and then select OKAY. 
Another window pops up saying TRANSFER COMPLETE OF 0.0KB.

I check my target board to see if the file is there but I can't see it if it is.
Is there a default folder my file would get transfered to?

Can anyone please advise me on how best to use the file transfer feature of Minicom?

I've googled this so much but it just keeps coming up with the manual which offers no real help. or from what I can make out.

Thank you again for your help,

Rob

---

### Post by jediborger on 2009-02-15
I would try installing the lrzsz package. It is not required but listed as recommended because it has tools for zmodem/xmodem/ymodem transfers.

I also have a beagleboard and am working on setting it up. Would you mind telling me how you set up minicom to work correctly? There is only one com port on my motherboard. One area that I am a little confused about is whether this requires a special serial cable. I have noticed references about a "null modem cable." What is that and does that mean a standard serial cable I have laying around won't work?

---

### Post by geraldm on 2009-02-15
The null modem changes the connections.
Normal use is for DTE device to be connected to DCE (modem) device. 
With the null modem two DTE devices can connect to each other.
Look up "null modem" in wikipedia for details.

---

### Post by HermanAB on 2009-02-15
Try Cutecom.

Cheers,

Herman

---

