---
title: "Can't login to Google Online Accounts"
date: 2017-04-28
forum: Desktop Environments
---

### Post by Nisuspi on 2017-04-28
I'm running Ubuntu 17.04 with Gnome Desktop installed, and running into a problem with Google in the Online Accounts settings. I can add a Google account in Unity, but it shows up when logged in to Gnome as an account for Jabber only (I don't have the options to sync calendar etc). 

If I delete that and try to add the account while logged into Gnome (now my primary desktop), I can only get as far as the password part of the login. The next windows, which should show the "Gnome wants access to..." dialogue is a blank page. The system log shows that the wizard is trying to connect (this message is repeated continuously: systemd-resolved[1592]: Using degraded feature set (TCP) for DNS server 127.0.1.1.). 

I've tried reinstalling both ubuntu and gnome online accounts packages, restarting the goa-daemon and even switching graphics drivers. Everything on the system is up-to-date.

---

### Post by mbrennwa on 2017-04-28
> **Nisuspi said:**
> I'm running Ubuntu 17.04 with Gnome Desktop installed, and running into a problem with Google in the Online Accounts settings. I can add a Google account in Unity, but it shows up when logged in to Gnome as an account for Jabber only (I don't have the options to sync calendar etc). 

If I delete that and try to add the account while logged into Gnome (now my primary desktop), I can only get as far as the password part of the login. The next windows, which should show the "Gnome wants access to..." dialogue is a blank page. The system log shows that the wizard is trying to connect (this message is repeated continuously: systemd-resolved[1592]: Using degraded feature set (TCP) for DNS server 127.0.1.1.). 

I've tried reinstalling both ubuntu and gnome online accounts packages, restarting the goa-daemon and even switching graphics drivers. Everything on the system is up-to-date.

I have not tried adding a Google account with Unity, but otherwise I have exactly the same issue (Ubuntu Gnome 17.04, brand new install on Dell XPS 13). The problem does not seem to occur on a different machine (older Acer laptop, upgraded from Ubuntu Gnome 16.10 to 17.04).

Is there a way to add Google accounts while this bug is being fixed?


EDIT: I just tried again on my older Acer laptop. The problem also exists there.

---

### Post by mbrennwa on 2017-04-29
I reported the bug here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-online-accounts/+bug/1687019?comments=all](https://bugs.launchpad.net/ubuntu/+source/gnome-online-accounts/+bug/1687019?comments=all)

Please add any useful information that helps fixing this bug.

---

### Post by speartip on 2017-04-29
Same problem here. Only happens on new logins from about 2-3 days ago.
I think something has changed on Googles end, as the login dialogue box has changed.

---

### Post by Hronom on 2017-04-29
Same

---

### Post by speediedan on 2017-04-29
Same. I've tried using an application-specific password as well (to exclude unlikely MFA contributions to the issue). No dice.

---

### Post by cartes2 on 2017-05-01
hi,

Someone found a work around but i didn't understand how it works :(

[https://bugzilla.gnome.org/show_bug.cgi?id=781990](https://bugzilla.gnome.org/show_bug.cgi?id=781990)

comment 4

Thank you for all the beug report done, sure it will helps to find the solution

---

### Post by cartes2 on 2017-05-01
Ok, i do understand how it works,

(sorry for my poor english)

First you need to change the way you connect to google. No more email but sms!
you have to go to google website in your account 
[https://myaccount.google.com/signinoptions/phone-sign-in/welcome](https://myaccount.google.com/signinoptions/phone-sign-in/welcome)

(connexion and security => connect to google)

Your android phone have to use this account. (google will send sms to this phone.) Then when you've finish this procedure , every time you'll connect something like a computer to google, you'll recieve a sms.
so now, in gnome online : add a google account, enter the mail adress then you will recieve a sms to confirm the conection ,and gnome don't need a password, it will connect.
Once gnome is connected, if you want, you can change the preference in your google account to use password instead of sms

That works like a charm :)

---

### Post by mbrennwa on 2017-05-02
> **cartes2 said:**
> Ok, i do understand how it works,

(sorry for my poor english)

First you need to change the way you connect to google. No more email but sms!
you have to go to google website in your account 
[https://myaccount.google.com/signinoptions/phone-sign-in/welcome](https://myaccount.google.com/signinoptions/phone-sign-in/welcome)

(connexion and security => connect to google)

Your android phone have to use this account. (google will send sms to this phone.) Then when you've finish this procedure , every time you'll connect something like a computer to google, you'll recieve a sms.
so now, in gnome online : add a google account, enter the mail adress then you will recieve a sms to confirm the conection ,and gnome don't need a password, it will connect.
Once gnome is connected, if you want, you can change the preference in your google account to use password instead of sms

That works like a charm :)

Hmm, that did not work for me. With 2 step verification i still have to enter my password. THEN I get the SMS code, and enter that to the Google login in addition to the password (if i login to Google using a normal web browser). But I never get the prompt for the SMS code with Online Accounts, I just get the blank window.

I reported the bug upstream ( [https://bugzilla.gnome.org/show_bug.cgi?id=781990](https://bugzilla.gnome.org/show_bug.cgi?id=781990) ). Please provide any info and details there, so they can get it fixed asap.

---

### Post by cartes2 on 2017-05-02
This is not 2 step validation but only SMS instead of e-mail. With 2 step you need password. Please follow my link

---

### Post by cartes2 on 2017-05-02
Hi,

[**[COLOR=#000000]@mbrennwa[/COLOR]**]("https://ubuntuforums.org/member.php?u=223184"): I've seen in then gnome beug report that the work around is working for you. Nice news :)

If you read the redhat beug report, it seems working  again today. It's strange.
[https://bugzilla.redhat.com/show_bug.cgi?id=1446817](https://bugzilla.redhat.com/show_bug.cgi?id=1446817)

---

### Post by speartip on 2017-05-02
Cartes2s fix in post 8 works for Unity & Gnome's online accounts.
However I've also found that Thunderbird no longer accesses Googles Accounts on XFCE, on new installs, even with the phone set up.
When the Google box comes up to enter your email/phone no. & then click next, nothing happens.

---

### Post by cartes2 on 2017-05-11
This is solved now in the proposed repository of webkit2gtk. It should be in the update in several days

For thunderbird, i had to install the very last version (52.1.0) from thunderbird website

---

### Post by Nisuspi on 2017-05-12
> **cartes2 said:**
> This is solved now in the proposed repository of webkit2gtk. It should be in the update in several days

Great news.

---

### Post by Nisuspi on 2017-05-15
Confirmed as working here after the GTK patch over the weekend. Thanks all.

---

