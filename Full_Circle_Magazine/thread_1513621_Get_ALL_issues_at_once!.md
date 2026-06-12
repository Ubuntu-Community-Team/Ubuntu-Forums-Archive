---
title: "Get ALL issues at once!"
date: 2010-06-19
forum: Full Circle Magazine
---

### Post by Jake007g on 2010-06-19
Ok, so I've seen a lot of people asking for a download including all issues so they don't have to download each once individually. Therefore I wrote a simple .sh script to help people out.

It basically creates a folder in your home folder called FullCircleMagazine and it will download all the issues starting with 37 and finishing with 0. It also renames a few of the issues so that they are all nicely organised.

Obviously you can add your own lines to incorporate issues released after this post.

Download the attachment, make sure it's checked to be ran as an executable and then run it in terminal.

Enjoy reading the issues. Major credits go to the developers of this e-Magazine, it's brilliant and is well worth reading if you haven't checked it out already!

---

### Post by ronniet on 2010-06-19
Cool, thanks for the script!  :)

---

### Post by belkinsa on 2010-06-29
I think it's missing issue 28, or at least for me.

---

### Post by cycling-rod on 2010-08-27
I too was missing issue 28? I got a 404 Not Found instead. Strange! Though I already have all the back-issues on my computer, I couldn't resist having a go at running the script (my first try at using a script), so thanks, jake0079.

---

### Post by Mnemic on 2010-09-06
> **Jake007g said:**
> Ok, so I've seen a lot of people asking for a download including all issues so they don't have to download each once individually. Therefore I wrote a simple .sh script to help people out.

It basically creates a folder in your home folder called FullCircleMagazine and it will download all the issues starting with 37 and finishing with 0. It also renames a few of the issues so that they are all nicely organised.

Obviously you can add your own lines to incorporate issues released after this post.

Download the attachment, make sure it's checked to be ran as an executable and then run it in terminal.

Enjoy reading the issues. Major credits go to the developers of this e-Magazine, it's brilliant and is well worth reading if you haven't checked it out already!

Thanks alot for that Jake007g!
Altho, i think there are some problems with that script.
As many users said, some Issues can't be downloaded.
Maybe the links are changed ? Im not really sure...
Anyways.. i'll post a fix for that, i modified the links abit to target the correct locations.
All credits to you :)
```

!bin/sh
cd ~
mkdir FullCircleMagazine
cd /media/FullCircle

wget http://dl.fullcirclemagazine.org/issue40_en.pdf
wget http://dl.fullcirclemagazine.org/issue39_en.pdf
wget http://dl.fullcirclemagazine.org/issue38_en.pdf
wget http://dl.fullcirclemagazine.org/issue37_en.pdf
wget http://dl.fullcirclemagazine.org/issue36_en.pdf
wget http://dl.fullcirclemagazine.org/issue35_en.pdf
wget http://dl.fullcirclemagazine.org/issue34_en.pdf
wget http://dl.fullcirclemagazine.org/issue33_en.pdf
wget http://dl.fullcirclemagazine.org/issue32_en.pdf
wget http://dl.fullcirclemagazine.org/issue31_en.pdf
wget http://dl.fullcirclemagazine.org/issue30_en.pdf
wget http://dl.fullcirclemagazine.org/issue29_en.pdf
wget http://test.fullcirclemagazine.org/wp-content/uploads/2009/08/fullcircle-issue28-eng1.pdf
wget http://dl.fullcirclemagazine.org/issue27_en.pdf
wget http://dl.fullcirclemagazine.org/issue26_en.pdf
wget http://dl.fullcirclemagazine.org/issue25_en.pdf
wget http://dl.fullcirclemagazine.org/issue24_en.pdf
wget http://dl.fullcirclemagazine.org/issue23_en.pdf
wget http://dl.fullcirclemagazine.org/issue22_en.pdf
wget http://dl.fullcirclemagazine.org/issue21_en.pdf
wget http://dl.fullcirclemagazine.org/issue20_en.pdf
wget http://dl.fullcirclemagazine.org/issue19_en.pdf
wget http://dl.fullcirclemagazine.org/issue18_en.pdf
wget http://dl.fullcirclemagazine.org/issue17_en.pdf
wget http://dl.fullcirclemagazine.org/issue16_en.pdf
wget http://dl.fullcirclemagazine.org/issue15_en.pdf
wget http://dl.fullcirclemagazine.org/issue14_en.pdf
wget http://dl.fullcirclemagazine.org/issue13_en.pdf
wget http://dl.fullcirclemagazine.org/issue12_en.pdf
wget http://dl.fullcirclemagazine.org/issue11_en.pdf
wget http://dl.fullcirclemagazine.org/issue10_en.pdf
wget http://dl.fullcirclemagazine.org/issue9_en.pdf
wget http://dl.fullcirclemagazine.org/issue8_en.pdf
wget http://dl.fullcirclemagazine.org/issue7_en.pdf
wget http://dl.fullcirclemagazine.org/issue6_en.pdf
wget http://dl.fullcirclemagazine.org/issue5_en.pdf
#wget http://fullcirclemagazine.org/download-manager.php?id=36
wget http://dl.fullcirclemagazine.org/issue4_en.pdf
wget http://dl.fullcirclemagazine.org/issue3_en.pdf
wget http://fullcirclemagazine.org/download/fullcircle-issue2-eng.pdf
wget http://fullcirclemagazine.org/download/fullcircle-issue01-english.pdf
wget http://fullcirclemagazine.org/download/Issue%200%20-%20English.pdf
#mv fullcircle-issue3-eng.pdf issue3_en.pdf
mv fullcircle-issue2-eng.pdf issue2_en.pdf
mv fullcircle-issue01-english.pdf issue1_en.pdf
mv fullcircle-issue28-eng1.pdf issue28_en.pdf
mv 'Issue 0 - English.pdf' issue0_en.pdf
```
PS: For a reason wget downloads two times the Issue 5.
One with a propper name, and one with "download-manager.php?id=36" as name. Commented out this one. :)

---

