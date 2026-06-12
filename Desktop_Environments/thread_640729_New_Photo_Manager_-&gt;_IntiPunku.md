---
title: "New Photo Manager -&gt; IntiPunku"
date: 2007-12-14
forum: Desktop Environments
---

### Post by irielion on 2007-12-14
Hi I made a new photo manager. It has many features that picasa has. Have a look at [http://intipunku.googlecode.com](http://intipunku.googlecode.com)

There is a release 0.1 look at the future features and give me suggestions. Im looking for co-developers and translators. Currently it is in english and spanish.

I attached some screenshots.

Comming features are:
    * Drag n Drop
    * Slideshow
    * Uploading photos to existing picasa album
    * Photo tagging
    * more on request 

I hope you guys can give me some feedback.

---

### Post by Jon &quot;Yogi&quot; on 2007-12-14
I think that you have a good interface thus far. I was wondering what kind of ideas you have to handle tagging. This seems like you have a good basis that you can build upon over time. Keep up the great work!

---

### Post by Steveway on 2007-12-14
Nice, didn't try it yet but I allready made a translation.
The german translation is attached here.

---

### Post by irielion on 2007-12-14
Hey thx for the comment, i planned tagging for 0.2 it has a high priority. Im still looking at some idea. What do you guys think? Something like gthumb or fspot?

---

### Post by Jon &quot;Yogi&quot; on 2007-12-15
I personally think that f-spot has a good layout.

---

### Post by irielion on 2007-12-15
I think it will be something like that. I will write the tags in XMP headers. THere will be panel, folderview/tags and eventually in other release i will also put a timeline.

---

### Post by peterthewolf on 2007-12-16
Does it put photos into readily accessible files
I find f-spot imitates ms crap by hiding my photos in unusable database

---

### Post by Jon &quot;Yogi&quot; on 2007-12-16
peterthewolf.. I would agree with you on that. But the interface of f-spot is fairly usable, IMO. Although a new intuitive interface, if anyone had some ideas, could be a nice change of pace.

---

### Post by irielion on 2007-12-17
Intipunku works as picasa. The database is your own photo directory. Modifications are saved automatically. However it saves the original in the directory Original in the album directory, just like Picasa.

I think fspot is totally unusable, because i dont tag my photos. I just want it to read directories. But fspot put everything in a timeline.

---

### Post by geoken on 2007-12-18
> **Jon "Yogi" said:**
> peterthewolf.. I would agree with you on that. But the interface of f-spot is fairly usable, IMO. Although a new intuitive interface, if anyone had some ideas, could be a nice change of pace.


I have an idea, show items in groups. 

This is a major failing of many Linux apps. When I want to view a group of items based on some filter criteria, it's extremely helpful to have some kind of visual separation between elements. 

 When I want to see pics from Jan. 07, I want to see the pics from Jan. 07. I don't want to see 2 rows of pics from the end of Dec. 06 (with one of those rows half cut off) then have the Jan. 07 pics start in the middle of a row they share with Dec. 07 pics. 

I look at it kind of like a book. Usually when a chapter ends, the remainder of that page is left blank and the following chapter starts on a brand new page. It's quite common for an entire page to be blank to serve as nothing more than a separator. Expanding on the book analogy, F-spot's UI would be equivalent to a book that switches chapters without even breaking the paragraph.

---

### Post by catach on 2007-12-18
You might find the digiKam [Date View](http://www.digikam.org/?q=node/14) to your liking, geoken. You can use the calendar widget to just see pictures from just a single date, or a week, or an arbitrary selection of days from that month, or the full month. It is quite nice.

---

### Post by kpkeerthi on 2007-12-19
I would like to see this evolve into a google picasa clone (features & usability) that runs **natively** in linux.

---

### Post by Jon &quot;Yogi&quot; on 2007-12-19
irielion, what file formats can you currently support?

---

### Post by geoken on 2007-12-19
> **catach said:**
> You might find the digiKam [Date View](http://www.digikam.org/?q=node/14) to your liking, geoken. You can use the calendar widget to just see pictures from just a single date, or a week, or an arbitrary selection of days from that month, or the full month. It is quite nice.

That is nice, I'm using gnome but that screenshot is really enticing me to use a non GTK app. I think in general the KDE guys feel the same way I do. The abilty to group items in Dolphin is something I've been waiting a long time for.

---

### Post by carlos1992 on 2007-12-19
it seems nice you should do something like a special way to look the pics or something to make special and not just other photo manager and also the pic after you handle it has a popular format (JPG,etc) cuz thats important but seems nice
PS. theres a town in el salvador with a name similar to your photo manager (intipuca, its beautiful)

---

### Post by peitschie on 2007-12-19
I'd be interested in helping in development.

Several features I'd like to see with regards to tagging...

1.  Ability to have a centralised database somehow... e.g., so photos tagged on one computer can be seen with all those tags from another computer *simultaneously*... maybe possible using a database backend?  I often work with a few other people with a lrage bunch of photos... there seems to be no way to share picasa albums across a network!  FRUSTRATING!

2.  Ability to build up "filters".  E.g., I click a keyword, then I can get a list of other keywords that photos with this keyword has, then I can add another etc., so that I end up with bread-crumbs.  This would be like a folder hierachy, except I could start from any folder in existence.  

For example, I have a few photos with the tags "2007","darwin","holiday".... I can navigate in any order I want to filter down the number of photos displayed.   E.g., 2007>holiday>darwin or darwin>holiday>2007 or holiday>darwin>2007 etc...  Each level showing ALL photos with the selected tags

3. Ability to link photos together in "revisions".  I do a lot of digital photography+graphics things, and often I will have a stock photo, then I will retouch it a few different ways (but I still want the stock photo!), then I will need to turn out a few different sizes depending on the application.... then I may crop it a few times.... I want to be able to link these all together in a kind of tree so I can keep the original (you never know when you want it untouched), and then also keep track of the touched up photos...

Anywho, that is counting chickens before one has even been created!  As I said, I'd be interested in developing, or helping with development.  Whats the best way to get involved?

---

### Post by irielion on 2007-12-20
Hi Im gonne try to answer the question.
For various enhancements bug I would like to refer to the websites issue page ([http://intipunku.googlecode.com](http://intipunku.googlecode.com)).
first concerning tagging. I just added the feature. I write IPCT tags. It is now functional, however currently to improve speed of startup everything is stored in a sql datebase. So that means that it doesnt detect tags added by other programs. Other programs will detect tags added by intipunku.
With tagging currently you can also see one tag at the time.. but with multiple selection that is implemented in notime. 
I currently only handle jpeg, because im not sure of formats like gif and stuff and their headers.
IntiPunku makes use of sort of revision, it backs up the original. But maybe we can implement something like that.
This calender widget sounds interesting, i will like to implement that.

---

### Post by irielion on 2007-12-20
Intipunku is a native latin american name, it is aymara or quechua, so maybe in some sense it is related all the way to el salvador.

---

### Post by eldragon on 2007-12-20
things i couldnt find in other photo managers i would love to see.

first: of course, tagging to work.

it should be able to handle your already existing hierarchy of storing photos. not mess with existing folders, names, etcetera. maybe handle all thumbs in an database-ish kind of thing for fast previewing.

it should have a screensaver plugin, where you pick which pictures to queue based on tags. THIS is a much desirable feature. 

multiple different ways of browsing your pics... (through nautilus, through album view, tag browsing, etcetera) this way you get to choose how to view everything.


and while we are at it:
```

tomas@emmet:~/Desktop$ intipunku 
Loading localization from po
Traceback (most recent call last):
  File "/usr/share/intipunku/intipunku.py", line 403, in <module>
    app  = IntiPunku()
  File "/usr/share/intipunku/intipunku.py", line 85, in __init__
    self.watcher = SunWatcher(self.albumdir, self.cachedir)
  File "/usr/lib/python2.5/site-packages/sunlib/utils.py", line 114, in __init__
    date = self.get_date(path)
  File "/usr/lib/python2.5/site-packages/sunlib/utils.py", line 152, in get_date
    data = EXIF.process_file(f)#, stop_tag="DateTimeOriginal")
  File "/usr/lib/python2.5/site-packages/sunextra/EXIF.py", line 1489, in process_file
    hdr.decode_maker_note()
  File "/usr/lib/python2.5/site-packages/sunextra/EXIF.py", line 1371, in decode_maker_note
    dict=MAKERNOTE_CANON_TAGS)
  File "/usr/lib/python2.5/site-packages/sunextra/EXIF.py", line 1161, in dump_IFD
    raise ValueError('unknown type %d in tag 0x%04X' % (field_type, tag))
ValueError: unknown type 768 in tag 0x0100

```

it started creating thumbnails an bam, it crashed. might help you debug  :)

---

### Post by irielion on 2007-12-20
Hey, normally i would ask you to post a bug on the project site. In this case I tell you to wait. In svn i dont use EXIF.py anymore, but pyexiv2. Next release i will provide packages for this. pyexiv2 will just ignore bad exif data. I think tomorrow i will have a release with packages. It will be a apt repositery this time.

---

### Post by irielion on 2007-12-28
Hey people, I need translators. 
I have translated myself in dutch, spanish and catalan. However I need people to revise this and people that can translate in other languages.

---

### Post by McNee on 2007-12-29
check out JuxtaPhoto - [http://jeffreyharrell.com/projects/juxtaphoto/](http://jeffreyharrell.com/projects/juxtaphoto/)

It has a couple nice features (possibly similar to Picasa and/or Flickr) where you build collections that include photos based on a list of tags, and it has a timeline view ability as well.

I'm playing with it installed locally using XAMPP, but having something that would also browse based on my existing folder structure would be a nice bonus.

---

### Post by irielion on 2008-05-25
Intipunku is maturing read my lastest blog and check out screenshots

---

### Post by markoloka on 2008-05-27
Is there possibility to change to next(or back) photo via mouse scroll button?? I like that feature in irfanview and i'm looking similar program for kubuntu. 
Tried digikam... it opened once but now it fails to open ever again.

---

### Post by irielion on 2008-05-27
I will implement that, it is easy to implement. Concerning Digikam, it would probably help if you destroy it config file, should be somewhere in .kde; However that is not the topic :S

---

### Post by markoloka on 2008-05-27
I'll test intipunku later today.

---

