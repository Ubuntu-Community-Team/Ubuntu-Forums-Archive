---
title: "ZFS email"
date: 2019-05-30
forum: Desktop Environments
---

### Post by dain-bramage on 2019-05-30
I am running Ubuntu 19-04 installed on RAID1 with mdadm.

I have installed postfix and configured the /etc/mdadm/mdadm.conf file to send me email notifications in the event of hard drive failure. I have verified this is working with:

```
sudo mdadm --monitor --scan --test -1

```
When I configured postfix on install I choose the "satellite" option as I will not be receiving emails, only sending.

I have also set up a ZFS pool and configured the /etc/zfs/zed.d/zed.rc file with the following changes:

```
ZED_EMAIL_ADDR="myemail@live.com"
ZED_EMAIL_PROG="mail"
ZED_EMAIL_OPTS="-s '@SUBJECT@' @ADDRESS@ -r [EMAIL="myemail@live.com"]myemail@live.com[/EMAIL]"
ZED_NOTIFY_VERBOSE=1

```
I have done "systemctl enable zed".

But I am not receiving any emails. "tail /var/log/mail.log" doesn't provide any insights.

Is there any way I can verify if ZFS is actually sending any emails?

"zpool events" doesn't indicate any email being sent. I have checked my spam folder.

---

### Post by TheFu on 2019-05-30
Did you validate that postfix can send email alone, from a shell?  ZFS/mdadm/logwatch are all going to assume the local MTA is working.  Test that first.  If email from a shell works, then we can move on to ZFS and other tools using the MTA correctly.

Most email systems will reject unauthenticated emails from random machines that aren't setup like normal internet email servers. That means they need to be on a business, static, network, have MX DNS records and probably have SPF DNS txt records too.  My email servers reject email from any where that doesn't have MX and SPF records and if it isn't on a static business network. Even rejecting all that email, I see hundreds of spam email attempts an hour, 24/7/365.  

If you are on a residential or DHCP subnet, pretty much every email service out there will consider it spam, assuming your ISP doesn't block the email from leaving their network first.

ISPs usually have an smtp-relay server setup somewhere that any of their subnets can use.  That would be a 1-line change in the main.cf postfix file, then restart postfix.  You'll need to search your ISP help pages for that **outbound email relay connection information**.  <--- that's what I would google with your ISP name in the search too.

If all your email goes to 1 address, then there is a [https://help.ubuntu.com/community/EmailAlerts](https://help.ubuntu.com/community/EmailAlerts) .
Before you setup this solution, consider what might be contained in system emails and why sending those to cloudy service providers, unencrypted, might be a less-than-great idea.  Unix logs often have very sensitive information included. Something to consider.

---

### Post by dain-bramage on 2019-05-31
Hi TheFu,

Thank you for your reply.

Wouldn't the fact that I am receiving emails from mdadm indicate that Postfix can send email and it is not being flagged as spam?

If I generate a test email with "sudo mdadm --monitor --scan --test -1" then check "tail /var/log/mail.log" I can see the email in the log but if I run a scrub then check "tail /var/log/mail.log" after completion of the scrub there is nothing.

It seems to me ZFS is not generating any emails despite zed being active:

```
[root@Ubuntu19-04:/home/mike# service zed status
&#9679; zfs-zed.service - ZFS Event Daemon (zed)
   Loaded: loaded (/lib/systemd/system/zfs-zed.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2019-05-31 00:39:54 NZST; 1 day 9h ago
     Docs: man:zed(8)
 Main PID: 9583 (zed)
    Tasks: 2 (limit: 4915)
   Memory: 2.6M
   CGroup: /system.slice/zfs-zed.service
           &#9492;&#9472;9583 /usr/sbin/zed -F

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.

```

I am wondering if the "/etc/zfs/zed.d/zed.rc" file has been configured correctly but from what I have seen on Google it appears to be correct?

---

### Post by TheFu on 2019-05-31
[https://askubuntu.com/questions/770540/enable-zfs-zed-email-notifications-on-16-04](https://askubuntu.com/questions/770540/enable-zfs-zed-email-notifications-on-16-04) says that  you have to have the **mail** client installed. Do you?
It is part of the ... heirloom-mailx package, I believe. It was in the mailutils package before, but ... 

To test, use **echo "TEST"| mail -s test you\@live.com **. If that works, then mail from zed should work. mail uses the local MTA configured.

---

### Post by dain-bramage on 2019-06-01
Hi TheFu,

Thank you for your response.

I have not installed "msmtp" because I was  following this post here which seems to indicate it is not necessary  (see 'finish06" post, click on the 'view entire conversation' tab to  access):

[https://www.reddit.com/r/homelab/comments/8c09pr/guide_to_setting_up_zed_to_email_alerts_for_zfs/](https://www.reddit.com/r/homelab/comments/8c09pr/guide_to_setting_up_zed_to_email_alerts_for_zfs/)


If I do **echo "TEST"| mail -s test you\@live.com **the response is:

```
Command 'mail' not found, but can be installed with:

apt install mailutils
```

This seems to be the problem. Why I get this error but finish06 does not is what I am trying to figure out. I have not installed 'ca-certificates' and neither have I added "smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt" to my /etc/postfix/main.cf file because I see the following entries there:

```
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

Apart from that I have followed the instructions exactly?

---

### Post by dain-bramage on 2019-06-03
Ok I got it working.

I had to install mailutils. I thought Postfix was a bit more stand-alone than that.

Thank you for your help TheFu.

For anyone wanting send mail via Postfix I found this post quite helpful.

[https://www.linode.com/docs/email/postfix/postfix-smtp-debian7/](https://www.linode.com/docs/email/postfix/postfix-smtp-debian7/)

---

### Post by TheFu on 2019-06-03
Happy you figured out a solution.

Postfix is an MTA. It works very well. This is not a mail client.  MTAs communicate with the outside world using SMTP. That's it.

ZED doesn't appear to have the right code to talk MTA language. Why should it when mail/Mail/mailx all exist and have for 40 yrs?  These other tools provide a CLI/shell interface to the MTA.

msmtp is a limited MTA. If you have that, you don't need/want postfix.

Please mark this thread as "SOLVED" using the thread tools button near the top. That helps the community greatly.

---

