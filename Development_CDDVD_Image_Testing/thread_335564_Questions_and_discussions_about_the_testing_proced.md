---
title: "Questions and discussions about the testing procedure"
date: 2007-01-10
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-01-10
Please post questions and comments here ...

---

### Post by bdmurray on 2007-01-10
What is the criteria for a Pass or a Fail?  Is it a matter of the install method working or not working?  Or does any failure in the [short test program]("https://wiki.ubuntu.com/Testing/Short") constitute a Fail?

---

### Post by Henrik on 2007-01-10
Good question!
(the answer is unfortunately not straight forward ...)

It basically fails if there is a release critical issue, and the threshold for that varies at different stages.

At Herd 1 everything was quite unstable, so when the installer worked for most people and didn't wipe anyone's drive we were OK to go. A non-working OpenOffice might even have passed at that stage.

For Herd 2 we want the overall quality to be higher, and so on for Herd 3, until Beta which we want to be as bug free as swe can get it. The same goes for RC really. But for final we will only fix really critical bugs and so cosmetic things will be deferred for later updates.

Hope that helps. Please ask if you are in doubt on a specific case.

---

### Post by davmor2 on 2007-01-10
May I recommend using sysinfo or hardinfo(i think is the alternative) to create a nice human readable hardware log file, setting up a separate section here where a copy of the log file can be pasted and then one copy of the hardware info for each tester is available.  It would just mean that if there was a regular fault you may be able to pin it down to a specific piece of hardware. Just a thought.

---

### Post by Henrik on 2007-01-11
Yes, perhaps they can do that in the post where they register and then blink to that post in the testing posts.

About PASS/FAIL: The important thing is to log the bugs you discover and then someone with more experience to judge it that qualifies as PASS or FAIL. Ultimately it's up to the release manager (Tollef) and the Ubuntu dev team lead (Matt Zimmerman) to decide when a release is ready to go.

---

### Post by Frak on 2007-01-11
How is the Image ID found? Sorry if this is a stupid question...

---

### Post by pochu on 2007-01-11
The ID is the number of the daily-build. When you download the daily-build, it is on a folder with the ID. For example, 20070111.1 (the latest at this moment on [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) )

Regards
Pochu

---

### Post by Frak on 2007-01-11
Yeah I figured it out, as if you uncompress the ISO and read the .disc file it contains the same text. Thanks.

---

### Post by STREETURCHINE on 2007-01-12
okay i think i may have goofed i downloaded the fiesty desktop iso overnight but for the love of it i cant find the version number,or is it hidden in a file somewhere.
i downloaded the daily build _(current)

if some one can tell me how to find the number it would be great

---

### Post by Frak on 2007-01-12
Unpack the iso to your desktop, then look at .disk, and open the file inside of it.

---

### Post by STREETURCHINE on 2007-01-12
i have uncompressed to desktop but could not find file called disk
it is not there.
unless it in side a folder but i have been looking for ages and cant find

---

### Post by Frak on 2007-01-12
Its not a file, its a folder, and it should be the first folder there.

---

### Post by STREETURCHINE on 2007-01-12
file ..folder same thing ,still not one here

---

### Post by STREETURCHINE on 2007-01-12
any one have an idea on this,i cant report till i have the number(be a shame not to file a report everything works great)  :D

---

### Post by pochu on 2007-01-12
Files and folders starting with a "." in Linux are hidden, so do ctrl+H to see the hidden items.

---

### Post by STREETURCHINE on 2007-01-12
nope still cant find,i am going to install any way if some one can tell me where the disk folder went to i will put the number in my report.
i downloaded last night with the latest daily build (12 th  january 2007)

---

### Post by pochu on 2007-01-12
The number is in the directory where you downloaded the nightly build. For example [http://cdimage.ubuntu.com/daily/20070111.1/](http://cdimage.ubuntu.com/daily/20070111.1/)

In that case, the ID would be 20070111.1

Best regards
Pochu

---

### Post by Rooy on 2007-02-15
Suppose your image is mounted on /cdrom
Open a terminal and:

cat /cdrom/.disc/info

That's all :)

Edit: of course that was .disk, not .disc

---

### Post by Fonzo on 2007-02-15
Hi there. 

I'm writing this post because I am beginning to consider the idea of downloading and installing the (last) Herd Image on my hard disk.

I have a HP compaq  nx9020 laptop with 256 MB ram, Celeron 1.40 GHz. 

I had been using Breezy first and then Dapper with a rather satisfying performance. The problems came when I decided to upgrade to Edgy. The upgrade crashed and I was not able to boot ever since. I have downloaded the Edgy desktop CD but the installation hangs even using vesa in xorg configuration.

So I'm guessing if I might get a try of a Herd image, given the fact that I have a Launchpad account and I think it wouldn't be too hard for me to report bugs, having a gained a little amount of experience using Ubuntu.

But I also think that if my installation goes well I will not perform another when the official release comes out, but will rely on updates.

So, what can you tell me about my purpose?

---

### Post by Fonzo on 2007-02-16
"Pre-releases of Feisty are *not* encouraged for anyone needing a
stable system [...] They are however recommended for
Ubuntu developers and those who want to help in testing, reporting,
and fixing bugs.  Installing a milestone and then upgrading through
the release cycle should leave you with a close approximation of the
final release." 

I just missed the [release announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-February/000247.html"). :)

---

### Post by pochu on 2007-02-16
Fonzo: if you need an stable system, do not use Feisty. But if you want to test and also to have an stable system, you can install dapper in one partition and feisty in another :D

Regards
Pochu

---

### Post by jerrylamos on 2007-02-17
http: address changed?  For the last week I've been doing just like the Wiki testing page said:
rsync -Lvv --progress rsync://cdimage.ubuntu.com/cdimage/daily/current/feisty-desktop-i386.iso .

The URL yesterday was: 
[http://cdimage.ubuntu.com/cdimage/daily/current/](http://cdimage.ubuntu.com/cdimage/daily/current/)

and is now: 
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) 

so I tried
rsync -Lvv --progress rsync://cdimage.ubuntu.com/daily-live/current/feisty-desktop-i386.iso .

which doesn't work: I get an error:

opening tcp connection to cdimage.ubuntu.com port 873
opening connection using --server --sender -vvL . daily-live/current/feisty-desktop-i386.iso 
@ERROR: Unknown module 'daily-live'

Does anyonw have an example of rsync that works today with the new URL?

Thanks, Jerry:confused:

---

### Post by pochu on 2007-02-17
Jerrylamos:

If you are using alternate (the first link you give is alternate CD)  try with this:
[http://cdimage.ubuntu.com/daily/current/]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by jerrylamos on 2007-02-17
Thanks for the reply to my post.

What confuses me is that Firefox gets to the same page using two different URL's:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and also

[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

The first URL doesn't work for me with rsync while the second one is running....

Thanks, Jerry:confused:

---

### Post by Juzz on 2007-02-27
please see here:

[http://ubuntuforums.org/showthread.php?p=2221244#post2221244](http://ubuntuforums.org/showthread.php?p=2221244#post2221244)

Am I just unfortunate with the amd64 images?

---

### Post by jtholmes on 2007-03-15
Is there a way to do the following during testing

Download an ISO image burn and test (I know how to do this one just fine )

Unpack ISO image to hard drive

Download current fixes (daily) and apply them to unpacked ISO Image on Hard Drive

Rebuild Live CD ISO image and Burn to CD and retest thus eliminating tons of download time

Just point me to the Wiki page as I have other uses for this procedure

---

### Post by jtholmes on 2007-03-15
setting email notifications only

---

### Post by pochu on 2007-03-15
> **jtholmes said:**
> Is there a way to do the following during testing

Download an ISO image burn and test (I know how to do this one just fine )

Unpack ISO image to hard drive

Download current fixes (daily) and apply them to unpacked ISO Image on Hard Drive

Rebuild Live CD ISO image and Burn to CD and retest thus eliminating tons of download time

Just point me to the Wiki page as I have other uses for this procedure
You can do that with RSync:

[https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)


Best regards
Emilio

---

### Post by j1mc on 2007-03-16
Should the md5sum come up correctly when you do an rsync update of the nightly images?  I've never been able to get a correct md5sum using rsync for xubuntu updates, and neither have some of the testers.  

i haven't received word of any successful md5sums after using rsync to update xubuntu images . . .

---

### Post by Henrik on 2007-03-16
Yes, the checksums should be correct. Are you sure you are getting the right chechsum file from the server. Have you tried this with a non-Xubuntu ISO? Perhaps there is a bug in the code that puts those files on the web (it has happened that checksums have been missing, for example).

---

### Post by j1mc on 2007-03-19
> **Henrik said:**
> Yes, the checksums should be correct. Are you sure you are getting the right chechsum file from the server. Have you tried this with a non-Xubuntu ISO? Perhaps there is a bug in the code that puts those files on the web (it has happened that checksums have been missing, for example).

I successfully rsync'ed the xubuntu live and alternate install cd's last night, but the checksums for the ubuntu and kubuntu ones failed this morning.  I'm just using the script that thornomad wrote.

I'll check those out this evening.

---

### Post by surdin on 2007-03-20
Is there any place... wiki page or what have you... where new people, like myself, can find out which log files are important to attach when reporting bugs or other problems for this testing project? Maybe someone could just add a list or something to the wiki page listing tests to perform? Or did I miss it somewhere?

---

### Post by pochu on 2007-03-20
> **surdin said:**
> Is there any place... wiki page or what have you... where new people, like myself, can find out which log files are important to attach when reporting bugs or other problems for this testing project? Maybe someone could just add a list or something to the wiki page listing tests to perform? Or did I miss it somewhere?
Read this ;)
[http://ubuntuforums.org/showthread.php?t=383067](http://ubuntuforums.org/showthread.php?t=383067)

Thanks
Pochu

---

### Post by jtholmes on 2007-03-20
I sync'd the  20070320  kubuntu 10AM EST today and all MD5
was fine. For Kubuntu that is.

I also selected
Check CD from ISOlinux menu and it was fine, that was not the
case yesterday.

---

### Post by jtholmes on 2007-03-20
This is pochu and henrik 

I filed at least 2 bugs earlier today against the installation cd

I was wondering if you gentlemen (and all this group of course)
would like me to post the  bug numbers here in case someone
would like to see if that particular bug has already been posted.


Also, I am afraid I have ventured out of my assigned area of testing

I was going to perform the  disk erase procedure and found out
that  auto resize crashed and burned and I started down that
rabbit trail. 

jt

---

### Post by Arby on 2007-03-21
Hi, 

I've been using Kubuntu for about a year and I've been looking for ways to get involved in giving a bit back. I've looked at signing myself up for testing a couple of times since this seems like something I could do. I just want to make sure I understand the process first to make sure I understand what I'm committing myself to. I don't want to commit to something I can't deliver. I've read the stickies on this forum and I've read the testing pages on the wiki. My understanding of what is involved is this, please correct me if I'm wrong.
1) Download the appropriate iso.
2) Check the md5sum matches the published value for that iso.
3) Burn the iso to cd.
4) Run the installation process.
5) Tick off as many of the items as possible on the Long test programme.

What I wasn't quite clear on is what happens with the results. If I find a bug, fine I file it on launchpad. What do I do if everything works fine, do I file a comment to say 'this iso is fine' or what? Also, roughly, what is the time committment involved?

I guess what I'm really asking is whether someone could walk me through the process the first time so I know I'm doing it right. I'm a Kubuntu user so I'd prefer to test in this area but I don't mind testing other flavours if there's a demand. I have a spare laptop I was intending to dedicate for this so I don't mind testing the cases that can potentially hose a system.

If someone can reassure me that I can do something useful then I'll sign myself up. I am Arby on IRC and Richard Birnie on Launchpad, although there's not much there yet.

regards,

Richard

---

