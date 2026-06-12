---
title: "PHP send email setup"
date: 2008-08-11
forum: Desktop Environments
---

### Post by syn4k on 2008-08-11
I'm curious how I can enable my server so that I can actually send email from it using PHP. I'm betting that setting up the server environment instead of the desktop would be adventageous but I've never tried that and my environment is already working perfectly aside from this mail issue.

I installed postfix:
sudo apt-get -y install postfix

I assumed that would fix it.

---

### Post by Xiong Chiamiov on 2008-08-11
You'll have to set up a whole [mail server]("https://help.ubuntu.com/community/MailServer") if you want to send mail completely from your server.  If you have a mail server you can use, you'll have to get the [SMTP settings]("http://us2.php.net/manual/en/mail.configuration.php") correct in your php.ini.

---

### Post by syn4k on 2008-08-22
Thanks for your response. I did set the value in the php.ini and yes, it was not set prior to this. I will continue to look into this.

---

