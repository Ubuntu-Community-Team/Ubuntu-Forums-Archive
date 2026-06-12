---
title: "Brasero reads new CD as Full"
date: 2009-02-06
forum: General Help
---

### Post by LindaLou on 2009-02-06
I'm not an experienced Brasero user but have had success with a few CD's I made for backup of particular files.  However, recently Brasero is telling me that the new CD I am trying to use is full.  Impossible as it is fresh out of the box.  This has happened with new 4 CD's - attempt to Add a file and Brasero says the disc is full.
As I mentioned I am not a seasoned with the program so am looking to find out exactly what I may have missed or if I am not alone!

---

### Post by tech9 on 2009-02-06
what kind of media is it?

---

### Post by LindaLou on 2009-02-06
The files are Open Office Word, Calc, Presentation some are MS Word, Excel, PP.  Basically, I need to back up my daily work files in these formats.  As well, I need to make CD's with these types of files for presentation purposes.

---

### Post by LindaLou on 2009-03-09
Still having the same problem with Brasero.  Anyone else? Any answers? This problem is exasperating in that a half empty disc with files of PDF format is just that, only half full!

---

### Post by DaveM59 on 2009-03-15
I just encountered the same issue trying to do a 1:1 disk copy of a data (photo) CD.  Brasero read the disk, created an image, then ejected with a message to remove it and replace with a blank CD.  I did this, but when the disk was inserted, I got the same error message you did -- disk full, aborting (or words to that effect).

I managed to make it work by splitting up the operation.  Instead of direct copy to a CD-R, I had the program create an image file in my home directory.  Then I closed the program, reopened, and selected Burn Image file.  I navigated to the file, selected it, and then, before inserting the blank disk, I selected a definite recording speed (32X) rather than the default "as fast as possible."  Then I inserted the disk, which the program recognized correctly as a blank, and the image was burned correctly.

You're trying to do something different so I don't have any specific advice for you.  I tried to do a file copy and could not get Brasero to work.  I resorted to the simple default CD Creator program.  This pops up automatically when you insert a blank CD-R in your drive.

---

### Post by LindaLou on 2009-03-18
DaveM59, Thanks for commiserating ! I am really choked with the cd burn programs with Ubuntu.  I will Gnome Baker, again.  I don't see the application you mentioned, in the Sound and Video (under Applicaitons). All I ever had from the get-go with 8.04 was Brasero.(UGH!!)  I browsed the Add/Remove Applications and found CD Play. Maybe this is what you were referring to in your post.  I install this as well and will give it a go. Thank goodness CD's are cheap, but still, it is frustrating and my CD collection is increasing!!:(

---

### Post by khelben1979 on 2009-03-18
Try with [K3b]("http://en.wikipedia.org/wiki/K3b") instead.

---

### Post by LindaLou on 2009-03-18
khelben1979, I've seen this K3b posted in other threads. One comment that I read is that it requires additional "dependencies".  No explanation was ever given as to what these dependencies were/are. Are you aware of any? I'm running Ubuntu 8.04 64 bit. 90% of the CD burning is Data - Oo Word, Calc, PDF files, etc.  Would like to burn music but just don't have the time anymore. I really need a CD burner that works "normally"!!  I have PDF catalogues that I need to send to clients on CD's.  These catalogues will have updates 2 - 4 times per year.  The PDF updates can be emailed and then the client downloads it onto the CD I sent.  This is just one application that I require a burner for but ALL applications require something other than Brasero that continually tells me that the CD is full when in fact it is not. Yup, I am frustrated!

---

### Post by khelben1979 on 2009-03-18
Go over at rpmfind.net and search for k3b. Then type this from a text console:
```
sudo alien [archive name].rpm
```
which should create a .deb archive for you.

```
man alien
```
for further help

The -c parameter converts scripts in the process when you convert it to a debian archive.

I'm not sure if this will work out, but I think it might be worth a try. Another alternative would be to build up from source code, but I don't think you want to do this.

---

### Post by LindaLou on 2009-03-20
khelben1979, Thanks for the instructions.  Before I try this, I would really appreciate some info as to what exactly this code would do. I don't have a problem with working with the code, but as I am still new to Ubuntu (not quite a year) I am hesitant.  Would you describe what exactly your code will do/perform and what steps I would need to take to complete or removed the application in question as well as any other info you might find necessary for a newbie.

---

### Post by avtolle on 2009-03-20
K3b may be installed from the Ubuntu repositories. Installing it in a Gnome environment will result in some KDE, i.e., Kubuntu libraries installed, which will take up space on your HDD, but when I've used it in the past didn't harm anything.

---

### Post by khelben1979 on 2009-03-20
Just follow the instructions. ;) It will not destroy anything on your system. (The worst thing which can happen is that you end up with conflicting packages)

If you feel uncertain I suggest that you try this first:
```
sudo apt-get install k3b
```

It's actually a lot better to use the apt-get command whenever possible then to take archives from rpmfind.net. It's a lot easier and will give you less hassle. Try it!

[Wiki about k3b]("http://en.wikipedia.org/wiki/K3b").

---

### Post by mitso on 2009-03-21
Im having the same problem. I want to copy a file to a disk and keep the disk open.
Ive tried:

CD/DVDcreator
Brasero
k3b
GnomeBaker

k3b rejected every disk I used - CD-R,CD-RW, and DVD+RW.

Brasero recorded the files but they were unreadable.

GnomeBaker and CD/DVDcreator made perfect copies but I found no way to keep them open.

And, no help from our friends here.

Let's keep trying ! I'm sure we'll find a solution.

---

### Post by mitso on 2009-03-21
Hi LindaLou,

I did get K3b to work by reducing the record speed from auto to 8gB. I'm adding files to Sony CD-R's.
The "CD/DVDCreator" program insists there is no space left on the disk, but somehow K3b finds some.

I also am fairly new to UBUNTU. I've been jumping in and out of LINUX for the past few years, but after 50 some odd years of IBM and Microsoft, I'm dedicating the rest of my years to UBUNTU - I'm only 88.

K3b does what I need, and from what you said I think it will do what you need. 

You can also download it from Synaptic Package Manager as well as the instructions of the 2 replies before mine - they obviously know much more about UBUNTU than I do.

I intend to dig deeper into K3b, and I'll let you know if I find any surprises.
I hope this works for you as it does for me.

---

### Post by LindaLou on 2009-03-24
thanks to all for advice and instructions. ;):p:D I will be installing K3b on my office PC.  It's a tough new HP computer with a good fast dual core processor and tons of ram and "stuff" that I know is important but don't know the lingo!:shock: I will post back with the results from my chosen form of install and let you all know how things work out.  Think I'll take the simple plan method. 
I will hold off on my installing K3b on my HP laptop as the processor, which is a pretty good one AMD64, seems to be overloaded with Ubuntu and some of the programs. Kinda weird how it seems to get overpowered sometimes when nothing is "working".  I never had too many processor issues with Windows but who's to say that a simple resolve could ease this issue. But that's for another posting!!
I am still wet behind the ears with Ubuntu - not quite a year yet - but I am pleased with the tremendous support!!  It was quite daunting to let go of Windows completely but I'm glad I did. I'll be posting back here in a couple of days.
 
Mitso, I think you follow the motto "You're as young as you feel!!" Always a pleasure to see that the Learned are with us.

---

### Post by mitso on 2009-04-03
Hi Again LindaLou

I've had a little more success with K3B.
But, I've found some inconsistencies that I haven't resolved.
On occasion, after saying it's writing, it will throw up a window saying the writing failed because I didn't have some right or other. In fact however it did actually record the file.
I modified one of those files and K3B replaced the original with the modified file.
There were some occasions when it refused to burn a file. That could have been my goof.
At this point I think K3B is the best of the programs I've tried. I would suggest, before you use it for real, take a few files and record, modify, rewrite, delete until you feel comfortable with the program.

Good Luck.

---

### Post by yosumi on 2009-04-03
I also had trouble burning files directly to a blank CDRW. It always says "not enough space" upon burning.

What I did was create an ISO using Brasero and then burn it as an image.

---

