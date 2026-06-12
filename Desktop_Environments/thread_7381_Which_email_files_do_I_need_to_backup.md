---
title: "Which email files do I need to backup?"
date: 2004-12-06
forum: Desktop Environments
---

### Post by Wok on 2004-12-06
Ubuntu looks great from the CD bootup, so I'm going to do a real install on a clean HD. I have mail and addressbook files in Evolution and Thunderbird that I need to keep, but can't tell from the filenames which ones contain the necessary data. Which ones do I need to copy to a floppy so I can restore them in Ubuntu Evolution? Also, what is needed to read the Thunderbird mail in Evolution?

---

### Post by JonAtkinson on 2004-12-06
Regarding importing Thunderbird email to Evolution, I think Thunderbird uses the Maildir format (have a look in $HOME/.thunderbird/), which can be imported into Evolution quite easily.

As for backing up the files, Evolution stores its mail in $HOME/.evolution/mail/local (get all the files in that folder), and it's address book in $HOME/.evolution/addressbook/local/system 

Disclaimer: It's not may fault if you miss something and lose data! :-)

--Jon

---

### Post by Defect0r on 2004-12-07
If you have space somwhere just grab your entire home directory
You can compress it first and then unpack it on the new install.
Do this from Outside your home directory.

tar -zcpf  /home/my_home_directory.tgz --directory /home/yourname/ .

This way you will be able to retrive all those other things you forgot.
Bookmarks, etc
 :D

---

### Post by wallijonn on 2004-12-07
With Evolution you can do an export to a file. With Thunderbird you have to backup the whole hidden directory (or at least the mbox folder / files).

[http://email.about.com/cs/evolutiontips/qt/et110103.htm](http://email.about.com/cs/evolutiontips/qt/et110103.htm)

[http://kb.mozillazine.org/index.phtml?title=Thunderbird_:_FAQs_:_Export_Outlook#Exporting_Thunderbird_email_to_Apple_Mail,_Outlook_and_Outlook_Express](http://kb.mozillazine.org/index.phtml?title=Thunderbird_:_FAQs_:_Export_Outlook#Exporting_Thunderbird_email_to_Apple_Mail,_Outlook_and_Outlook_Express)

[http://texturizer.net/thunderbird/faq.html](http://texturizer.net/thunderbird/faq.html)
.

---

### Post by sandyeggoboy on 2006-03-25
I have an issue with my backup .. i did a full copy of the files in my home dirrectory, including hiddens, to a seperate partition on the hard xdrive and then did a clean install. command was **sudo cp /home/deric/* /mnt/other/ -r**
What command do i need to use in order to copy my stuff back so i can keep my permissions, instead of the root user?:confused: 

Thanks in advance.

Deric

---

### Post by frank002 on 2007-10-24
I use Thunderbird e-mail and need to know how to backup the address book. Would appreciate instructions. Thanks

---

