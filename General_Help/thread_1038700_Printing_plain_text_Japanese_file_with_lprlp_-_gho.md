---
title: "Printing plain text Japanese file with lpr/lp - ghostscript, postscript issue?"
date: 2009-01-13
forum: General Help
---

### Post by 655 on 2009-01-13
I use the handy rsstail program to parse news feeds in Japanese for a few choice headlines, and I would like to put this behavior in a crontab so that it can print the article content for me every morning or so.

Everything is working fine, and I'm able to pull down the content and display it in the command line and output it to plaintext files.  When I try to send these files to the printer (if relevant, it's a Samsung ML-1630N laser), only the non-Japanese, plain ASCII text prints, with large white space where the Japanese 2-byte characters should be.

I'm not really sure what is the source of the problem, because I don't understand ghostscript and postscript fully.  I can print rich text documents like .doc, .odt, .pdf and content from the web in Japanese with no problems.  So I assume I'm missing a crucial step when doing this through the command line.

Is it because, by just piping a text file to the printer with lpr, my printer doesn't have Japanese fonts internally supported?  Is it because I need to route the output through ghostscript or postscript first?  Is it a locale issue?  I found some information that looked promising on a Debian mail archive ([http://osdir.com/ml/linux.debian.user.japanese/2002-06/msg00009.html](http://osdir.com/ml/linux.debian.user.japanese/2002-06/msg00009.html)), but what I tried did not work.  The "Basics of Japanese Printing" located here ([http://tlug.jp/craigoda/writings/linux-nihongo/node69.html](http://tlug.jp/craigoda/writings/linux-nihongo/node69.html)) are 
similarly inscrutable and likely outdated.

I've monkeyed around with LPRng, enscript, ghostscript, the printcap file, magicfilter, (as far as I know, many of these alternatives are deprecated) trying to set a locale setting, create a .ps or pdf out of the content before piping it to the printer, but so far, I can only 
print garbage.

What key step am I missing here? Could someone point me in the right direction?  Thank you.

---

### Post by 655 on 2009-01-15
Bump :confused:

---

### Post by KeyserSoze93 on 2009-01-15
I realised I'd like to know this too, so I found this:
[http://www.mail-archive.com/debian-user@lists.debian.org/msg472275.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg472275.html)

do ```
sudo apt-get install paps
```

then:
```
cat YourJapaneseDoc.txt|paps|lpr
```

It just turns your document into postscript, which can be understood by lpr.

Works perfectly, the prints look great (though the font is a touch big for newspaper articles, it looks like there's an option to change the font)

---

### Post by 655 on 2009-01-15
Omigod thank you!  UTF-8 to ps, of course.  I'm so glad this can be done with one app.

It printed perfectly, and it is a bit large, but the articles aren't especially long -- and Japanese text is a bit easier on the eyes when pumped up in size.

My only followup is that some characters in the text are randomly bold. (see attached)  Did you experience this?

---

