---
title: "Ubuntuforums Fails W3C Validation"
date: 2008-01-18
forum: Forum Feedback &amp; Help
---

### Post by brennydoogles on 2008-01-18
[http://validator.w3.org/check?uri=www.ubuntuforums.org&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=www.ubuntuforums.org&charset=%28detect+automatically%29&doctype=Inline&group=0)

---

### Post by atoponce on 2008-01-18
Does this produce improper functionality on the forums for any browsers?

---

### Post by Luggy on 2008-01-18
> **atoponce said:**
> Does this produce improper functionality on the forums for any browsers?

This is Linux we are talking about here. We don't care about functionality, all that matters is standards!

---

### Post by bonzodog on 2008-01-18
yeah, this unfortunately is vbulletin, the forums software that does it. The people that write it don't seem to be overly worried about standards

---

### Post by ~LoKe on 2008-01-18
So?

---

### Post by happysmileman on 2008-01-18
> **bonzodog said:**
> yeah, this unfortunately is vbulletin, the forums software that does it. The people that write it don't seem to be overly worried about standards

I don't suppose there'd be any point using an open source forum so it could be made standards compliant legally, after all, it's not like there's any compelling reason for a Linux distributions's forum to use Open Source software.

---

### Post by matthew on 2008-01-18
> **happysmileman said:**
> I don't suppose there'd be any point using an open source forum so it could be made standards compliant legally, after all, it's not like there's any compelling reason for a Linux distributions's forum to use Open Source software.[http://ubuntuforums.org/showthread.php?t=176622](http://ubuntuforums.org/showthread.php?t=176622)
and
[http://ubuntuforums.org/showthread.php?p=5088](http://ubuntuforums.org/showthread.php?p=5088)

I've used several forum packages. vBulletin has the best features and stability of any that I have seen. It really isn't a contest. Other forums admins seem to agree: [http://www.theadminzone.com/forums/showthread.php?t=45305](http://www.theadminzone.com/forums/showthread.php?t=45305)

---

### Post by Christmas on 2008-01-18
This doesn't really matter so much. It's the same as in C or any other programming language. Take for example the fact that in ANSI C comments starting with '//' are not allowed, but the binary produced by the compiler is exactly the same in either way. As long as the result is the same this shouldn't matter.

---

### Post by brennydoogles on 2008-01-18
I actually just thought it was funny. I have been going through and making sure all of my sites were compliant, and I decided to check if several sites I use regularly were as well. Ubuntuforums (as well as homestarrunner) were not. Just an FYI.

---

### Post by sowelie on 2008-01-18
I will be honest I can't figure out why anyone uses vBulletin.  I set it up for a customer and I assumed (wrong) that it would run fine on a windows server.  It ran like the database was connected to the server dial up and half a world away, even though the mysql install was located on the same server.  I set up phpBB on the same box, and it ran perfectly with the same amount of data.  People say vBulletin's admin is better, but I think it was hideous and clunky.

---

### Post by ~LoKe on 2008-01-18
The Ubuntuforums are actually pretty close to compliant.  Have a Look at Ubuntu.com and see how far they're off.

---

### Post by vexorian on 2008-01-18
I think you assumed wrong that a windows server would run correctly  ;) .

vBulletin is a great product, no doubt of it.

But it is not open source, and in all seriousness SMF is really doing a great job lately... ... but if instead of SMF you compared it with phpbb, invision, yabb, and many others it is seriously no contest, those three ones are just terrible boards, I've seen many forums and I actually think there is a correlation between success and using vBulletin or at least SMF, mostly because some of the other board software is terrible. Specially YABB, I 've seen that one kill entire web sites after migration to it.

But if you wanted to stick with vBulletin, read this: You CAN make it follow the standards, just needs some tweaking in templates and the bbcode code... I know the sort of hacks to vBulletin this forum runs, so I don't think it is so hard...

---

### Post by matthew on 2008-01-18
FYI, although vBulletin is not open source (eg. not GPL or BSD licensed or similar), the source is viewable by anyone who has paid for a license. It can also be modified on a local level, if you don't care about upgrade compatibility, but you can't release the changes. Anyway, from a tin-foil-hat security standpoint, vBulletin is still okay because anyone who has paid for a license has full access to all the source code and can audit at will.

The only people I know of that have used vBulletin and not liked it are people like the poster above, who have tried to install it on Windows servers.

Everyone I know that has run both fully open source forums and vBulletin on a Linux platform has fallen in love with vBulletin.

If people like/love and want to use phpbb, SMF, or others, that's totally cool with me. To each his own. I think it depends on the site you are running, the features you need, and your own personal taste as well (and maybe your pocketbook...).

Anyway, we are taking this thread way off topic. Sorry about contributing to that...  Let's get back to discussing the amusing fact that our forums are not fully W3C compliant. ;)

There is a new vBulletin release that we will upgrade to fairly soon. Perhaps it will be W3C compliant. I have seen the previews, and it will include some incredibly useful new features, so we are pretty excited about that...hopefully web standards compliance is among them. :)

---

### Post by popch on 2008-01-18
> **bonzodog said:**
> (...) vbulletin, the forums software that does it. The people that write it don't seem to be overly worried about standards

The OP and the report linked to names a number of coding errors resulting in malformed (not well formed) HTML markup.

These are bugs, and surprisingly few for a page as complex as those produced by vbulletin.

They do not imply anything about 'standards compliance' of the product. They imply even less about the commitment to standards or the lack of such commitment.

These are just bugs. They can be fixed. They probably get fixed as soon as the developers become aware of them.

Next, you will be accusing sun of non-compliance with HTML standards, because part of the java class class documentation published on the web is even less well formed than the HTML code produced by vbulletin.

---

### Post by brennydoogles on 2008-01-18
I was not bashing Ubuntuforums for being non-compliant... I know that sometimes that is not possible. I have a page on my site that will NEVER validate because it links to a photo album on Facebook, which uses a link scheme that is non-compliant (from what I can tell the = sign in the URL produces an error). I just thought it was funny that a forum populated by so many Geeks was non-compliant.

---

### Post by vexorian on 2008-01-18
> **brennydoogles said:**
> (from what I can tell the = sign in the URL produces an error)



Something is telling me that your problem is about & and not = and that it is fixable.

---

### Post by Bruce M. on 2008-01-18
[CENTER]**If it ain't broke, don't fix it!**[/CENTER]

OK the forums opening page had Validation Output:  5 Errors, and the forum works just fine.

However:

 1. [Microsoft]("http://validator.w3.org/check?uri=www.microsoft.com&charset=%28detect+automatically%29&doctype=Inline&group=0"):  Potential Issues: 1 and Validation Output:  32 Errors.  :-({|=

 2. [Google]("http://validator.w3.org/check?uri=www.google.com&charset=%28detect+automatically%29&doctype=Inline&group=0"): Potential Issues: 2 and Validation Output:  47 Errors

All in all, I think vBulletin is doing just fine. =D>

Keep up the good work guys!  :KS:KS:KS:KS:KS

---

### Post by brennydoogles on 2008-01-19
> **vexorian said:**
> Something is telling me that your problem is about & and not = and that it is fixable.

I'm not sure what the problem is... [Here]("http://validator.w3.org/check?uri=http%3A%2F%2Fbrenny.brennyandangi e.com%2Fphotos.html&charset=%28detect+automatically%29&doctype=Inline&group=0") is the validator page for the page on my site that won't validate. I also noticed today that the W3CSchools site is not valid either. I love it!! I think it's so funny that sites like MSN.com can get it right, and the W3c cannot.

---

### Post by p_quarles on 2008-01-19
The Debian forums only have 1 validation error. :D

In all seriousness, 5 errors is nothing. Get the "Web Developer" Firefox extension and do W3C validation on the sites you visit. You'll see that it's not unusual for fully working web sites to have upwards of 100 validation errors. None is rare. 5 deserves a medal.

---

### Post by LaRoza on 2008-01-19
> **p_quarles said:**
> The Debian forums only have 1 validation error. :D

In all seriousness, 5 errors is nothing. Get the "Web Developer" Firefox extension and do W3C validation on the sites you visit. You'll see that it's not unusual for fully working web sites to have upwards of 100 validation errors. None is rare. 5 deserves a medal.

I pride myself on valid code, but I occasionally have errors. My home page has one (which I am going to fix when I update the page)

Opera has "validation" in the right click menu, very handy.

---

### Post by vexorian on 2008-01-19
> **brennydoogles said:**
> I'm not sure what the problem is... [Here]("http://validator.w3.org/check?uri=http%3A%2F%2Fbrenny.brennyandangi e.com%2Fphotos.html&charset=%28detect+automatically%29&doctype=Inline&group=0") is the validator page for the page on my site that won't validate. I also noticed today that the W3CSchools site is not valid either. I love it!! I think it's so funny that sites like MSN.com can get it right, and the W3c cannot.

W3CSchools != W3C.

Although I think you might be speaking of their forum software.

Anyways, a quick look at your errors page tells me it is all about using & in addresses.

For example, you have:

```

<a href="http://etsu.facebook.com/album.php?aid=2002075&l=23e9b&id=57504548">Album 1</a><br />

```

Instead it should be:
```
<a href="http://etsu.facebook.com/album.php?aid=2002075&amp;l=23e9b&id=57504548">Album 1</a><br />
```

---

