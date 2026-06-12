---
title: "Searching files and files contents - no luck yet"
date: 2011-10-19
forum: Desktop Environments
---

### Post by ElQanah on 2011-10-19
Ok.  I have dozens of .odt and thousands of .docx, .slxs. etc.

Basically I use Ubuntu (*11.10 now) and for starter, the Unity Search Files and Folders is a failure.  Do not even find files by name part.  Nautilus Search seems to find those at least.

But it's critical for many users like me to be able to search documents contents.  I have found that scream for help in many places googling about that issue, but no successful stories, except for Google Desktop for one guy somewhere.

Google Desktop was half working for the last two Ubuntu releases.  Now they closed the project "because everybody is clouding their data".

Last time I tried Beagle, it did nothing for me on Nathy, neither Tracker was a successful tool for the job.

I ran into DocFetcher, but haven't tried that yet (any suggestions are highly appreciated).

---

### Post by WB0HYQ on 2011-10-20
I am with you ElQanah.  In unity I am unable to get a single match even with "*.*".  NOTHING shows up.  I know I have around 1200 pictures (JPGs) and no search parameters can find them - even though they are in my Pictures folder.

Basically, I am not able to find any of my files and have not found a single "file manager" that works properly.

Any help out there?

Bill

---

### Post by DZ* on 2011-10-25
> **ElQanah said:**
> I have dozens of .odt and thousands of .docx, .slxs. etc.

I switched from Google Desktop to recoll. It is very powerful. It can do complex queries, restrict search to filetypes, and it can even do stuff like search within zipped PDF attachmments to emails, which Google Desktop couldn't do. It doesn't do real time indexing by default, although it has that capability too. You'd have to tell it to update the index or setup a cron job (recoll documentation explains all that).

---

### Post by WasMeHere on 2011-10-25
I had not heard of ***recoll***, it makes me interested :-)

Don't forget that there are powerful command line tools to run from a terminal window: try the following commands to learn about ***find*** and ***grep***.
```
info find
info grep
```
Having fun finding out about Ubuntu
Olle

---

### Post by Matt 6:27 on 2011-10-25
Beagle used to be pretty good, if hard on your system resources.

It's not graphical, but I find 'locate' quite effective to find files or directories.

Go to Terminal and update your database:
  [INDENT]*sudo updatedb*[/INDENT]

Once updated, search for file:
[INDENT]*locate -i [search term]*[/INDENT]
The "-i" eliminates case sensitivity in the search.

To find terms within a file, use:
[INDENT]*grep [search term] **[/INDENT]

*= wildcard - I believe you should be able to substitute the * with a filename to narrow the search.

There a ton of ways to narrow a search, so check out "man locate" or "man grep" in terminal.... and good luck.

---

### Post by DZ* on 2011-10-25
> **Olle Wiklund said:**
> I had not heard of ***recoll***, it makes me interested :-)

Don't forget that there are powerful command line tools to run from a terminal window: try the following commands to learn about ***find*** and ***grep***.
```
info find
info grep
```Having fun finding out about Ubuntu
Olle

These are good for simple tasks, within a small number of files. Some advantages of recoll are instantaneous search, search for content other than simple text (sure, one can feed grep the output of something like pdftotext, but it quickly gets complicated), and ability to click on results to open in an application.

Another thing it is good at is "stemming", and not only in English. For example, in addition to English stemming I have set it up to return results for inflected/derived forms of Russian words and recoll does this job very well.
For a fresher version of recoll than that in repos,
```
sudo add-apt-repository ppa:recoll-backports/recoll-1.15-on
```

---

### Post by Matt 6:27 on 2011-10-25
> **DZ* said:**
> These are good for simple tasks, within a small number of files. Some advantages of recoll are instantaneous search, search for content other than simple text (sure, one can feed grep the output of something like pdftotext, but it quickly gets complicated), and ability to click on results to open in an application.

Another thing it is good at is "stemming", and not only in English. For example, in addition to English stemming I have set it up to return results for inflected/derived forms of Russian words and recoll does this job very well.
For a fresher version of recoll than that in repos,
```
sudo add-apt-repository ppa:recoll-backports/recoll-1.15-on
```


DZ - sounds good.  I think I'll take a look at recoll too. Thanks.

---

### Post by ElQanah on 2011-11-10
> **DZ* said:**
> I switched from Google Desktop to recoll. It is very powerful. It can do complex queries, restrict search to filetypes, and it can even do stuff like search within zipped PDF attachmments to emails, which Google Desktop couldn't do. It doesn't do real time indexing by default, although it has that capability too. You'd have to tell it to update the index or setup a cron job (recoll documentation explains all that).

Thank you for your recommendation.  I installed recoll and it's quite impressive.  Definitively the way to go, best option so far, fast and reliable.  Better of what I expected.  

Now that's linux working well!

---

### Post by opiumpoetry on 2012-03-08
**Docfetcher** works great for me. Sure works better than "Search for Files..." which only finds half what it should.

---

