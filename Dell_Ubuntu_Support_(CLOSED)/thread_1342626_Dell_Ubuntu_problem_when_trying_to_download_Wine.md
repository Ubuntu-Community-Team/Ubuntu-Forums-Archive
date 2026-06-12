---
title: "Dell Ubuntu problem when trying to download Wine"
date: 2009-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by prophessor on 2009-12-01
I tried downloading the wine application so I can download windows programs but when I tried downloading it from the site's way:

Open the Software Sources menu by going to System->Administration->Software Sources. Then select the Third Party Software tab and click Add.

Then, copy and paste one of the lines below depending on which version you are running.

For Ubuntu Karmic (9.10):
ppa:ubuntu-wine/ppa

Click close to finish, and then reload the package information when prompted. If you have Wine installed, the system's update manager will now inform you of the latest Wine beta release and prompt you to upgrade. If you haven't installed Wine yet, go to Applications->Add/Remove and search for Wine or just click this link.



So I do all that but when I get to the end where I click that link or do it the searching way I get this message:

"Can not install 'wine' (E:Unable to correct problems, you have held broken packages.)"

---

### Post by gbrainin on 2009-12-01
I don't know why you need to add a repository (the part where you're adding ppa:ubuntu-wine/ppa), since wine is available in the standard repositories.  Try deleting that line and using Add/Remove Programs.  If the new repository is set up for beta releases, that could explain the broken dependencies.

You may not get the most recent version of Wine (this week's), but I haven't had any problem installing Wine from the regular repositories in several versions of Ubuntu.

---

### Post by ugm6hr on 2009-12-02
> **prophessor said:**
> "Can not install 'wine' (E:Unable to correct problems, you have held broken packages.)"

Sounds like you have installed some "broken" packages.

Will need to find out what's going on from Terminal: post the output from all the following:

```
sudo apt-get update
sudo apt-get install -f
```

---

