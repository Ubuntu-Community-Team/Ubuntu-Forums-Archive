---
title: "Compilations/How-tos (A separate edition)"
date: 2008-09-09
forum: Full Circle Magazine
---

### Post by fiddler616 on 2008-09-09
I think it'd be really cool if FCM published a separate edition:
a)Each time a series ended. For example, they'd have up a pdf that was entitled "Howto: Set up your own server", and was all the articles on that pulled from all the issues.
b)That was a collection of 'regulars'. "The last 5 top 5s" "Half a year of Ubuntu Women", "Featured Letters", etc.
Because, like, when I pull myself together and learn how to use the GIMP, it'll be a lot easier to just have one document. Also, I remember reading a Top 5 about blogging tools, but I didn't have a blog then, and now I can't remember what issue it's in, and can't be bothered to search through the last 10.
I mentioned this to onlineapps, who told me to put it in the forum, but he said that:
> That's also a good idea, though it would make more sense to have "a year's worth" or something like that.
Though he'll probably show up on this thread anyway.
So what do the grand powers of Full Circle think?

---

### Post by deicidist on 2008-09-09
I think that's an excellent idea. In fact, I'd even be willing to attempt to compile it if no one else volunteers to do so!

I've recommended tutorials published in FCM to others (in fact, I recently told a roommate who was curious about Scribus to check it out - despite being a Windows user, she's all about the open source software, lol).

It would be **SSSOOOOO** nice to be able to find an entire HowTo or series in a single special edition issue.

---

### Post by ronniet on 2008-09-10
> **deicidist said:**
> I think that's an excellent idea. In fact, I'd even be willing to attempt to compile it if no one else volunteers to do so!


Feel free!

You'll need some sort of PDF app to chop and splice the pages though. But really all you'd need to do is go through the issues, chop out all the Scribus articles then splice them together in to one PDF, email it to [email]admin@fullcirclemagazine.org[/email] and he'll put them on our downloads page. Same with the Server series.

My GIMP series still has about two more parts to it.

And, if you feel adventurous, do the 'year in review' thing. Chop all the Top5s out of #01-12 and splice them together in one PDF. Same for Ubuntu Women.

**Good luck!**  :KS

---

### Post by ronniet on 2008-09-10
> **fiddler616 said:**
> Also, I remember reading a Top 5 about blogging tools, but I didn't have a blog then, and now I can't remember what issue it's in, and can't be bothered to search through the last 10.

You're looking for FCM#04 for the **Top5 Blogging Tools**.

[https://wiki.ubuntu.com/UbuntuMagazine/FullIssueIndex](https://wiki.ubuntu.com/UbuntuMagazine/FullIssueIndex)
:KS

---

### Post by RobinC@Amethyst on 2008-09-10
> Originally Posted by fiddler616 View Post
Also, I remember reading a Top 5 about blogging tools, but I didn't have a blog then, and now I can't remember what issue it's in, and can't be bothered to search through the last 10.

You can find the article listing on the Full Circle wiki under

[https://wiki.ubuntu.com/UbuntuMagazine/FullIssueIndex]("https://wiki.ubuntu.com/UbuntuMagazine/FullIssueIndex")

Listing for #16 will go up later in the week.
RC

---

### Post by fiddler616 on 2008-09-10
Thanks ronniet for the issue number, thanks RobinC for the Issue guide (I never knew about that...it'd be a nice touch to mention it on the very last page of issues), and thanks all of the above for being so supportive.
If somebody tells me which PDF chop/splice app to use, I'll be perfectly willing to make a 12 months of Top 5s, or Year of Ubuntu Women, or whatever's needed. Just point me in the right direction.
Mark as solved?

---

### Post by DJ_Peng on 2008-09-10
Awesome idea! My sis and I were talking about wanting a compilation of the Scribus tutorial series last year. Can either Scribus or OpenOffice.org(3) open the PDF files and let you cut and paste the appropriate articles?

---

### Post by ronniet on 2008-09-10
> **fiddler616 said:**
> Thanks ronniet for the issue number, thanks RobinC for the Issue guide (I never knew about that...it'd be a nice touch to mention it on the very last page of issues), and thanks all of the above for being so supportive.
If somebody tells me which PDF chop/splice app to use, I'll be perfectly willing to make a 12 months of Top 5s, or Year of Ubuntu Women, or whatever's needed. Just point me in the right direction.
Mark as solved?

You could try PDFedit, not sure if it does pages, but it does allow editing of PDF text: [http://pdfedit.petricek.net/pdfedit.index_e](http://pdfedit.petricek.net/pdfedit.index_e)

DEB file available from GetDEB: [http://www.getdeb.net/](http://www.getdeb.net/)

If possible, try and have: [www.FullCircleMagazine.org](www.FullCircleMagazine.org) on each page, just so people know where the pages came from, and to expand our readership.

**Thanks!**
:KS

---

### Post by fiddler616 on 2008-09-10
Either I'm missing something important, or:
* The PDFedit download page doesn't include and Ubuntu-friendly format (ergo the getdeb link)
* getdeb doesn't have it:
[http://www.getdeb.net/search.php?keywords=PDFedit](http://www.getdeb.net/search.php?keywords=PDFedit)

---

### Post by ronniet on 2008-09-10
you could try this one (for Hardy): [http://download.tuxfamily.org/3v1deb/pool/gutsy/3v1n0/pdfedit_0.3.2-1~3v1ubuntu1_i386.deb](http://download.tuxfamily.org/3v1deb/pool/gutsy/3v1n0/pdfedit_0.3.2-1~3v1ubuntu1_i386.deb)

---

### Post by onlineapps on 2008-09-10
Install pdftk. It includes a merge tool. Here's a command on how to do it:

pdftk issue1.pdf issue2.pdf issue3.pdf

---

### Post by ronniet on 2008-09-10
> **onlineapps said:**
> Install pdftk. It includes a merge tool. Here's a command on how to do it:
pdftk issue1.pdf issue2.pdf issue3.pdf

...but can it merge specific pages from specific issues into a new PDF?? :confused:

---

### Post by deicidist on 2008-09-10
Pdftk is amazing. Command-line only, but very useful. And to answer your question, Ronnie, yes it can:

First, use the 'Burst' utility to separate all the pages of the magazine into separate PDF files. (I recommend doing all of the following in a separate folder, so you don't get lost if there are many pages to sort through!)

pdftk in.pdf burst

Then delete the pages you don't need. Do this for each magazine containing the content you wish to merge. When that's finished, you can use the following command to merge all of the separate pages into a single PDF file. (since the command I'm using uses a wildcard, make sure that there is no other content than what you need in this folder as it will merge EVERY pdf in the folder)

pdftk *.pdf cat output combined.pdf

Note that the above command combines all the PDFs in that folder in alphabetical order. Be sure that your documents are named in the order you wish to merge them if you do this!

For more info, check the man-pages!

---

### Post by onlineapps on 2008-09-10
Haha... was about to say no :-P

---

### Post by deicidist on 2008-09-10
> **onlineapps said:**
> Haha... was about to say no :-P

lol

Where there's a will... :P

---

### Post by ronniet on 2008-09-10
> **deicidist said:**
> Pdftk is amazing. Command-line only, but very useful. And to answer your question, Ronnie, yes it can

Well, what are you waiting for, Christmas? **Get to it!**  ;)  :KS

---

### Post by deicidist on 2008-09-10
Hahaha, don't worry! I'm already all over this one! Expect a few drafts in the next week or so!

I should add that I'm not just looking to merge a few pages from pre-published work. I want polished, proper looking special editions. I'll start with my personal favourite (Scribus) and work from there!

---

### Post by deicidist on 2008-09-10
So... I did a quick job of compiling the individual pages (in PDF format) and merged the entire 30-page Scribus How-To compilation into a single file.

The result?

I have a 161MB file called Scribus.pdf that looks great, works and has everything. The problem is, it's 161MB.

pdftk turns each individual page into a file that is just under 6MB, when it merges them, that's all it does. I turned to the man-pages and found a compress option. I tried it, hoping for the best, and got a second 161MB file.

Any ideas?

(Not a big deal, I still intend to do it properly, but it'd be nice to know how to do this for later!)

PS- If anyone wants a copy of the 161MB Scribus.pdf file, send me a message, or find me on the #fullcirclemagazine channel!

---

### Post by onlineapps on 2008-09-10
Did you post on the pdftk mailing list or forms (if they have any)?

---

### Post by deicidist on 2008-09-10
Not yet. I'll do that this weekend when I'm not so busy. lol

---

### Post by Sef on 2008-09-10
> **Compilations/How-tos (A separate edition)**

That's going to be really nice.

---

### Post by ronniet on 2008-09-11
> **deicidist said:**
> 
PS- If anyone wants a copy of the 161MB Scribus.pdf file, send me a message, or find me on the #fullcirclemagazine channel!

Whoa boy, hang on to the PDF for now, don't distribute it. I'll create a special FCM front cover for each special issue.

161mb is a tad harsh! The size may be something to do with the images in the articles? Not sure. But still... it shouldn't be 161mb! Each issue with 35+ page is only about 6mb!  :(

Yeah, I agree with Andrew, time to check their mailing list/irc channel.

**Thanks!**

---

### Post by deicidist on 2008-09-11
I should have clarified, "If anyone wants a copy - to try and fix the compression issue - let me know." lol

But no worries, I've deleted it anyways. Decided to start fresh. ;)

---

### Post by onlineapps on 2008-09-11
Ronnie, the old issues had a different template anyway. It might be a good idea to recreate in Scribus anyway.

Do you have the Scribus templates? If you do, I might be able to do something.

---

### Post by fiddler616 on 2008-09-11
Speaking about the weekend, it's coming up, so let me know before then if/what I should do.

---

### Post by ronniet on 2008-09-11
> **onlineapps said:**
> Ronnie, the old issues had a different template anyway. It might be a good idea to recreate in Scribus anyway.

Do you have the Scribus templates? If you do, I might be able to do something.

Yep, all the files are stored on the Ubuntu wiki:
[http://wiki.ubuntu.com/UbuntuMagazine](http://wiki.ubuntu.com/UbuntuMagazine)
... under TRANSLATIONS.

---

### Post by deicidist on 2008-09-11
Great! Downloading them all right now. Thanks Ronnie!

---

### Post by TheIdiotThatIsMe on 2008-09-24
Can't wait to see :)

---

### Post by fiddler616 on 2008-12-16
Has this thread/concept died? Or are people just quietly working away?

---

### Post by deicidist on 2008-12-16
It's still alive... At least I still have full intentions of working on a few to start. My company recently started a new contract that requires more work hours and a lot more traveling (thankfully it pays well!), so I've been quite busy. As soon as I have a polished product, it'll be published ASAP! ;)

---

### Post by fiddler616 on 2008-12-17
> **deicidist said:**
> It's still alive... At least I still have full intentions of working on a few to start. My company recently started a new contract that requires more work hours and a lot more traveling (thankfully it pays well!), so I've been quite busy. As soon as I have a polished product, it'll be published ASAP! ;)
Sweet. Thank you.
Good luck with your new job!

---

### Post by ranch hand on 2008-12-17
Just came across this thread and was interested by it.  Sounds good.

PDFedit, by the way, is in Synaptic, at least for Hardy.

---

