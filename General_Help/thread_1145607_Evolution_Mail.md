---
title: "Evolution Mail"
date: 2009-05-01
forum: General Help
---

### Post by Amerigo777 on 2009-05-01
I cannot get Evolution Mail to work with my Yahoo or Hotmail accounts.   For Yahoo it says, "unhandled Yahoo! Mail mailbox (unknown fetchyahoo failure)"   For Hotmail it says, "unhandled Windows Live Hotmail mailbox (cannot execute "GetLive": Failed to execute child process "GetLive" (No such file or directory))"  Gmail works fine.  What I real want is a Linux mail handling application like Pop Peeper that notifies when new mail is received and allows you to read/manage it in a window, rather than opening my browser. The point is, I don't want to visit the sites. Pidgin does the same as Evolution, so Evolution is pointless really. Unless it can open emails in it's own window....

---

### Post by cmnorton on 2009-05-02
It may have changed, but in order to get access to Yahoo's pop and smtp servers, you have to pay them an annual fee. It's like $20.00 a year. You cannot just send email through their servers without paying them; at least it used to be like that?

---

### Post by codeseer on 2009-05-02
> **Amerigo777 said:**
> I cannot get Evolution Mail to work with my Yahoo or Hotmail accounts.   For Yahoo it says, "unhandled Yahoo! Mail mailbox (unknown fetchyahoo failure)"   For Hotmail it says, "unhandled Windows Live Hotmail mailbox (cannot execute "GetLive": Failed to execute child process "GetLive" (No such file or directory))"  Gmail works fine.  What I real want is a Linux mail handling application like Pop Peeper that notifies when new mail is received and allows you to read/manage it in a window, rather than opening my browser. The point is, I don't want to visit the sites. Pidgin does the same as Evolution, so Evolution is pointless really. Unless it can open emails in it's own window....

Do you have a premium Yahoo! mail account? If not, it doesn't normally allow you POP access.

Source: [http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-35.html;_ylt=A0WTTC74efxJh7wA5TwKzyN4](http://help.yahoo.com/l/us/yahoo/mail/original/mailplus/pop/pop-35.html;_ylt=A0WTTC74efxJh7wA5TwKzyN4)

Are you using these settings for Hotmail? 

[http://lifehacker.com/5151551/hotmail-enables-pop3-for-us-users](http://lifehacker.com/5151551/hotmail-enables-pop3-for-us-users)

There's also the old way: [http://www.ubuntugeek.com/how-to-configure-evolution-to-use-hotmail-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-configure-evolution-to-use-hotmail-in-ubuntu-810-intrepid-ibex.html)

---

### Post by Amerigo777 on 2009-05-02
Thank you very much.  Is there a way to get things like Evolution and Pidgin to start automatically when booting/rebooting the computer?

---

### Post by dcstar on 2009-05-02
> **Amerigo777 said:**
> Thank you very much.  Is there a way to get things like Evolution and Pidgin to start automatically when booting/rebooting the computer?

System-Preferences-Startup Applications

---

### Post by jrz on 2009-05-29
I use evolution for gmail, hotmail, and yahoo mail. Both gmail and hotmail now have free pop access, but I have to use fetchyahoo (not the old one in Synaptic) but the latest one you dl from the source, and from cron it retrieves my yahoo mail into the mbox and I then set evolution to retrieve the yahoo mail from my mbox when it schedules to run. I believe there is a "how to" for ubuntu on how to accomplish all this, and it's not terribly difficult.

---

### Post by David2009 on 2009-05-30
I am glad to hear that you're having success with gmail and hotmail.  What are the settings that you use in Evolution? 
 
Thank you!

David

---

### Post by jrz on 2009-05-30
For gmail:
Identity tab
    email address: {name}@gmail.com
Receiving Email tab
    Server type: POP
    Configuration
        Server: pop.gmail.com:995
        Username: {name}@gmail.com
    Security
        Use Secure Connection: SSL encryption
    [checked] Remember password
Receiving Options
    Your choices
Sending Email
    Server type: SMTP
    Server configuration
        Server: smtp.gmail.com:465
        [checked] server requires authentication
    Security
        Use Secure Connection: SSL encryption
    Authentication
        Type: PLAIN
        Username: {name}
    [checked] Remember password


Hotmail (essentially the same as above except:)
Receiving email server: pop3.live.com
Username: {name}@hotmail.com
AND
Sending email server: smtp.live.com

I also use yahoo free access, but that requires fetchyahoo or a similar program, and it retrieves the mail into my mbox, and then I fetch it to evolution by setting the Receiving server type to "Local delivery", giving the path to where fetchyahoo has stored the mail.

---

### Post by TRANQU111TY on 2009-07-04
Firefox has a add-on that checks for mail on gmail, hotmail, yahoo and more. No need to pay any annual fees and it is as easy to configure, as it is to install it.

---

### Post by kaligus on 2009-09-22
fetchyahoo works most well for me.

but you do need to use classic mail on the web interface, and keep up-to-date with fetchyahoo because yahoo periodically changes something and the author needs to tweak to get it right again.

---

### Post by ~Las~ on 2009-10-25
Uninstall repo version of fetchyahoo.Get new from [http://sourceforge.net/projects/fetchyahoo/](http://sourceforge.net/projects/fetchyahoo/) .Extarct to your home folder and make a link to /usr/bin from file fetchyahoo  (you ll need to become su)(only that file) and it will work.It does for me:).This is till repo ver get updated.Then remove link and install from repo.

---

