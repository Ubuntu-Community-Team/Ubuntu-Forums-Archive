---
title: "Exporting contacts from Mac Addressbook to Evolution"
date: 2008-09-28
forum: Desktop Environments
---

### Post by Timo Laine on 2008-09-28
I am migrating from Mac OS X 10.4 Tiger to Ubuntu and I have been able to transfer most of my data, but I am having a hard time trying to import Mac Address Book contacts to Evolution. Address Book outputs vCard data, but Evolution does not accept the exported file. I guess the data is not completely standard vCard or Evolution just can't handle vCard really well. I have also tried third party utilities to export the contacts in csv format, but with no success in importing that data.

I have also exported the data to Gmail, but I lose some data fields when exporting again from Gmail to Evolution.

Any ideas?

---

### Post by chuckd1356 on 2008-09-28
I would also like to know how to do this. 

I've been unsuccessful in my attempts so far. (Obviously)

---

### Post by heluani on 2008-10-26
Hi guys, I'm not sure if you're still having this issue, but I was having that problem and I read somewhere that it had to do with the fact that the vCards in Addressbook.app got exported encoded as UTF-16 regardless of the encoding you use. So it is a matter of converting the file's encoding to UTF-8. I couldn't do this on my box for some reason. The converter just adds the character '^@' to every character. So the solution in my case was just to erase those characters with a simple ```
sed -e '-s /^@//g'
```

And now evolution sees the contacts, pictures and everything!, hope this helps you...

R.

---

### Post by Timo Laine on 2008-10-29
Thanks for the advice. However sed did not work for me. Instead I had to use the command

```
iconv -f utf-16 -t utf-8 oldcards.vcf > newcards.vcf
```

The idea is obviously the same, to convert utf-16 to utf-8. After this everything seems to work, although I haven't double checked all the cards and fields.

---

### Post by heluani on 2008-10-29
That's funny, that was my first try and with iconv was that I got these extra bytes '^@' for each character.

Glad to hear it worked!

R.

---

### Post by hictio on 2008-10-29
Very cool, I'll give a try soon, as I had to all sorts of tricks to export my contacts to Evolution (Some where on an Outlook box...)
One question, I use a lot the "Note" section of each contact on Address Book.app, how does this gets exported?
On my present export, the Notes did got it thru Evolution, but there is also some text added, like this

Directory Server:Normal
Government ID Number:Sin especificar
Private:Normal
Profession:Falso

Does this happen using this method?

---

### Post by joekwme on 2009-01-10
Hi All,

Not entirely new to ubuntu, but not a hardcore warrior yet either.

Trying to go 100% linux.  Got everything installed, and really need to migrate my data over to evolution.

Safari bookmarks imported fine.  My evolution calendar works too.  Have a hard time importing mac addressbook into evolution.  I still have to import email, too. 

When I get the imported file the evolution assistant does not recognize the .vcf file containing my addresses--the "next" button is shaded.

I saw the thread at [http://ubuntuforums.org/showthread.php?t=932207](http://ubuntuforums.org/showthread.php?t=932207), and tried to using iconv to convert from UTF-16 to -8, and even renamed the file, but still no luck.  The sed command is something I'm clueless about, and did some googling, but still unsure how to use it.

Any ideas?

Thanks

Joe> [QUOTE][/QUOTE]


After a few hours I decided to try to trysome freeware for the MAC called A to G.app.  It organizes your addressbook into csv files and using that I imported into evolution.

thanks

---

### Post by grinsekatze on 2009-05-26
Hi everybody,

I've migrated to Ubuntu with my MacBook some months ago. After some trouble with the installation of parts of the MacBook hardware, it has now become my preferred OS. So coming across the topic of this thread was a matter of time, I guess.

I didn't know, that the MacOSX Addressbook was saving it's vCard-files in UTF-16 encoding, so I tried Timos iconv suggestion. Unfortunately it ended up in a few chineese-looking symbols and an error message. I did a little further research and found, that the MacOSX Addressbook saves its vCard-files in UTF-16 big endian. Passing this little piece of information to iconv (which seams to use little endian as standard), solved the problem for me. The command would be

```
iconv -f utf-16BE -t utf-8 -o newvcard.vcf oldvcard.vcf
```Hope this helps. Cheers

---

### Post by g999b on 2011-04-29
Hi Everybody
Thanks for all the posts, all interesting but ... one question: you seem to be handling all these .vcf files one by one, am I correct?
I have more than 300 contacts on my Mac, dont tell me I have to repeat the operations 300 times :(

---

### Post by tomek_wap on 2011-10-25
> **g999b said:**
> Hi Everybody
Thanks for all the posts, all interesting but ... one question: you seem to be handling all these .vcf files one by one, am I correct?
I have more than 300 contacts on my Mac, dont tell me I have to repeat the operations 300 times :(

@[grinsekatze]("http://ubuntuforums.org/member.php?u=843359") - you solution was good for me. thank you!  now I need to check if all data was being correctly exported/imported into Evolution, so I don't a have a situation where some data/fields are missing - oh well, as I thought, most fields are imported OK, apart from the notes, which are listed in Evolution as separate contacts ... thus having over 700 contacts instead of 380. At least most data was being exported/imported.

As for the 300 contacts, when exporting from Mac, you need to select all contacts in Address Book, and save vcards info one file.

---

