---
title: "Thunderbird in KDE"
date: 2008-05-03
forum: Desktop Environments
---

### Post by Gannin on 2008-05-03
I recently started using Kubutnu, and I'm loving it.  I find myself far preferring it over Ubuntu.  It looks nicer, it's faster and more responsive, I can set all my options through the normal GUI instead of having to dig through gconf, and the fonts are much better.  I'm even enjoying using Konqueror as my web browser.

My question is, I installed Thunderbird from the repos to do my e-mail.  No matter how I fiddle with its settings, when I click on a link in Thunderbird it doesn't open that page in Konqueror.  Is there something I'm overlooking, or do I just have to start using KMail to get that functionality?

---

### Post by CREEPING DEATH on 2008-05-03
It's probably trying to open a Mozilla browser, buyt I'm not sure how to change it.

CD

---

### Post by sstusick on 2008-05-03
I had this problem also on KDE with Thunderbird. About a week after installing it, all of a sudden Thunderbird started opening the links in Firefox, it's really weird lol.

---

### Post by Gannin on 2008-05-03
I know that Thunderbird will respect whatever default browser settings you have in Gnome and open the appropriate browser accordingly, but it doesn't seem to care about whatever default browser settings you have in KDE.  I'm guessing Thunderbird is looking for the settings in gconf, which of course KDE doesn't have or use.

---

### Post by warp99 on 2008-05-03
> **Gannin said:**
> I know that Thunderbird will respect whatever default browser settings you have in Gnome and open the appropriate browser accordingly, but it doesn't seem to care about whatever default browser settings you have in KDE.  I'm guessing Thunderbird is looking for the settings in gconf, which of course KDE doesn't have or use.

Here's a link on how to do this:

[http://gentoo-wiki.com/TIP_Integrate_Thunderbird_and_Firefox](http://gentoo-wiki.com/TIP_Integrate_Thunderbird_and_Firefox)

You can also go into the about:config settings in Thunderbird and Firefox and add handlers that way if you prefer.

---

### Post by Gannin on 2008-05-04
Thanks for the help.  That worked great :).

---

### Post by bturig on 2008-07-12
In Kubuntu 8.04, using Thunderbird 2.0.0.14 and Firefox 3.0, I got it to work by changing the http handler in Thunderbird.

From the Thunderbird menu go to 
Edit->Preferences->General Tab->Config Editor

Set the key network.protocol-handler.app.http = /usr/lib/firefox-3.0/firefox

---

