---
title: "Connecting two ubuntu pc's to share folders"
date: 2009-02-07
forum: General Help
---

### Post by arepaking on 2009-02-07
Hello,

I have two computers at home running Ubuntu. I am in the need to transfer a 5GB file from one computer to another but I do not find the proper way to do this. I am still learning about Ubuntu as I write this message.

I would like to share a folder in computer "A" so computer "B" can be able to access it and copy the file from there.

Could somebody help me to make the corresponding configuration in both computers?

Thank you very much in advance,
ArepaKing

---

### Post by avtolle on 2009-02-07
Does [http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/) help?

---

### Post by arepaking on 2009-02-07
> **avtolle said:**
> Does [http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/) help?

Hi,
Thanks for your reply. I tried that approach but I keep getting this error message:
```

Error: Timed out when logging in
Please select another viewer and try again.
```

---

### Post by avtolle on 2009-02-07
I have that problem when one of my computers is using wireless, but not when connected with an ethernet cable. Perhaps that might help you?

---

### Post by arepaking on 2009-02-07
Both computers are wireless, but thanks for your suggestion. However, I found the error. I just had to add a new policy in the firestarter firewall program to allow incoming connections from my other computer by using the port "22".

When I disabled the firewall it worked.. 

Thank you for your help; SSH is definitely the best way to go. I am glad to announce that my 5GB file is being transmitted to my laptop as I write this message.

Cheers,
AK

---

### Post by GammaRay256 on 2009-02-07
Install "openssh-server" on one of the computers.  On the other, go to "Places>Connect to Server" and choose type "SSH".  Enter the other computers IP address and your username (and optionally, for server, /home/[yourusername]).  When you connect, it will ask for your password.  You will get a file browser of the other system.  You can copy and paste to the SSH folder as if it were a local folder.

This is not the only way to do this, and it doesn't exactly use shares.  But it should accomplish what you are trying to do.

_**EDIT:** I didn't actually read the link above, but it looks like what I'm describing here.  Sorry about the repeat.  Glad to hear it worked out in the end._

---

