---
title: "Google Chrome Pdf plug-in missing"
date: 2010-05-13
forum: Desktop Environments
---

### Post by kawshik84 on 2010-05-13
Hi,

Whenever I trying and open a pdf file in google chrome it shows a blank screen and says pdf plugin missing. However, firefox on the same machine works fine and shows pdf files.

I am a newbie to Ubuntu so please provide a detailed solution.

thanks.

---

### Post by lovinglinux on 2010-05-13
Try [gPDF](https://chrome.google.com/extensions/detail/egljjohbmnnpicoiddaapkpejfpnmmpe) extension. I use the Firefox version and it works great.

---

### Post by kalyp on 2010-05-14
Same problem here. And it's a lucid problem, it worked fine in karmic yesterday.
The problem with the viewers involving google docs is that they change the url, adding [https://docs.google.com/viewer?url=](https://docs.google.com/viewer?url=) before it. I have a lot of PDF on the web linked from my computer but with their real URL... so gPDF doesn't work. And even in other cases (when adding the [https://docs.google.com/viewer?url=](https://docs.google.com/viewer?url=)) I sometimes get the message "Sorry, we are unable to retrieve the document for viewing".

In short, I'd like to understand what is wrong with chrome, pdf and lucid :) if anyone has an idea I'm interested. 
Thanks.

---

### Post by pgn674 on 2010-06-10
I had the same problem. So I opened up about:plugins in Google Chrome, clicked the details button in the top right, and did a page search (Ctrl+F) for "pdf". I found that mozplugger was installed somehow and set to handle .pdf files, so I used Synaptic Package Manager to uninstall that. Now PDFs open inside Firefox OK, and in Chrome it offers to save it as a file - no more need to right click and save link as.

Still looking to see if there is any way to view PDFs inside Chrome in Ubuntu.

Edit:
If you can't figure out what package is providing a given plugin, then copy the file name at the end of the location field in about:plugins, and use dlocate in terminal to find out which package provided that file. There might be another way other than dlocate, but I forget what it was.

---

### Post by victorfuts on 2010-07-27
> **kawshik84 said:**
> Hi,

Whenever I trying and open a pdf file in google chrome it shows a blank screen and says pdf plugin missing. However, firefox on the same machine works fine and shows pdf files.

I am a newbie to Ubuntu so please provide a detailed solution.

thanks.

this is because google tries to use it's own pdf viewer rather than using external plugins.

what i do is simply disable viewing pdf in chrome:

1.go to : chrome://plugins/
2.disable "Chrome PDF Viewer "

after u done this, pdf will be downloaded.

---

### Post by pgn674 on 2010-07-27
> **victorfuts said:**
> this is because google tries to use it's own pdf viewer rather than using external plugins.Actually, kawshik84 posted his question on May 13th, and the embedded Chrome PDF Viewer became [available]("http://blog.chromium.org/2010/06/bringing-improved-pdf-support-to-google.html") June 17.

I'm not sure how far it's been released for Linux so far, but right now the stable version (Google Chrome 5.0.375.99) doesn't have it at all. Beta / dev versions may have a nonworking entry for it in about:plugins, so if other people get the gray screen error, victorfuts's idea is a good one to check.

---

### Post by infestor on 2010-08-20
> **pgn674 said:**
> Actually, kawshik84 posted his question on May 13th, and the embedded Chrome PDF Viewer became [available]("http://blog.chromium.org/2010/06/bringing-improved-pdf-support-to-google.html") June 17.

I'm not sure how far it's been released for Linux so far, but right now the stable version (Google Chrome 5.0.375.99) doesn't have it at all. Beta / dev versions may have a nonworking entry for it in about:plugins, so if other people get the gray screen error, victorfuts's idea is a good one to check.

you are right, there is no PDF viewer plugin in chrome, so that solution does not work

---

### Post by infestor on 2010-09-02
any updates on the issue? is there an official or working plugin available yet?

---

### Post by kalyp on 2010-09-03
Actually I don't know about the plugin, but I just googled again this issue this morning and found [http://www.google.com/support/forum/p/Chrome/thread?tid=543f0c80bace6c42&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=543f0c80bace6c42&hl=en)
I tried the "popular answer" and it works!!

---

### Post by koenr on 2010-09-10
Thanks for the tip - solved my problem too

---

