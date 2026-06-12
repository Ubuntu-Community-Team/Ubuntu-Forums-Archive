---
title: "CLI Web interface"
date: 2009-02-16
forum: General Help
---

### Post by monsterstack on 2009-02-16
I've been meaning to work out how to do this for a while. In short, I'd like to make a cli-style interface to my website. But I don't really know where to begin. I've rudimentary javascripting know-how, but the syntax is familiar *enough* to Python that I think I could learn as I go if I had to. Ideally I'd like to avoid javascript (I browse with noscript 24/7), but I guess that's probably not possible.

I found a somewhat crude implementation [here](http://www.thewebsiteisdown.com/) (click on the unix icon), but checking out the page source, it seems to be one massive script. I'd like to try and avoid huge, unmanageable scripts; perhaps making a script to pull in text from other files is a possibility? I was thinking perhaps having a small frame at the bottom of the window to control another, larger frame above.

So yes, nothing too fancy. Just using basic bash commands to list directories for blog style postings, perhaps cat'ing them to display them or something. It'll be horribly inaccessible to 90% of web users, but then I'm not intending the site to be generally famous or anything so I'm okay with that.

Can anyone give me a few pointers on how to start going about this? I've searched for help, but the online documentation I have found is a bit too daunting: I mean I'd rather not have to learn any more javascript than I have to, seeing as I never use it for my offline projects.

---

### Post by mb_webguy on 2009-02-16
I did something like this a while back for a computer science club website using PHP (and liberal use of the exec function).  I basically wrote a limited web-based shell.  Unfortunately, I lost this (along with most of the other web sites I'd created in the previous 8 years) when my computer crashed a couple of years ago.

The important thing to consider when doing something like this, whether you use PHP or Javascipt, is security.  If you blindly allow command execution on your server, you're basically sending out invitations to crackers to invade your system and holding the door open for them as they arrive.  Limit access to a specific directory tree, and parse input carefully to make sure the user isn't trying to sneak commands through.

---

### Post by fragos on 2009-02-16
Making a separate CLI version isn't really required. Install lynx or elinks and surf your site with them. The trick is to insure that you create proper ALT tags in IMG markup to describe the images which aren't seen in text browsing. This is by the way the view of your site that web crawlers like that of Google have. Sites implemented in Flash are a problem since the text content is all in images. You won't have Javascript either. Your links will still be functional in text browsing.

I hand code my sites using HTML, CSS, Javascript and PHP. They are quite usuable by text browsers and well understood by web crawlers. This activity will also result in a more Serach Engine Optimized site. I can't speak to the lack of control over text browsing that may exist in higher level tools other than in some instances these tools can make your site unvistable by some systems -- even mobile devices with sufficient screen real estate to view any site.

---

### Post by Phlee on 2009-02-16
> **fragos said:**
> Making a separate CLI version isn't really required. Install lynx or elinks and surf your site with them. The trick is to insure that you create proper ALT tags in IMG markup to describe the images which aren't seen in text browsing. This is by the way the view of your site that web crawlers like that of Google have. Sites implemented in Flash are a problem since the text content is all in images. You won't have Javascript either. Your links will still be functional in text browsing.

I hand code my sites using HTML, CSS, Javascript and PHP. They are quite usuable by text browsers and well understood by web crawlers. This activity will also result in a more Serach Engine Optimized site. I can't speak to the lack of control over text browsing that may exist in higher level tools other than in some instances these tools can make your site unvistable by some systems -- even mobile devices with sufficient screen real estate to view any site.

He's got the right idea.

---

### Post by monsterstack on 2009-02-17
Thanks for the feedback.

PHP, hrmm? I was afraid of that. I have zero experience with php. My server supports it, though. I'm not really interested in my site being particularly search-engine friendly, though.

[Here](http://cb.vu/) is an utterly amazing example of the sort of thing I'd like to achieve. This guy has opted for a ridiculously detailed shell, complete with its own vi clone and tab completions. It has all sorts of stuff in there (type *ls /bin* for the full list).

My site would not be quite so detailed. SSH mock-up? I don't think so! I only need ls and cat commands to get started. Arbitrary execution of random shell code shouldn't be a problem, as obviously *cat $some-files* would only be able to spit out text from a few text files in a certain directory on my server. Looking through the source of that guy's site, it seems listing directories only displays text contained within the script, which is fine for me. *cat*ting them displays text from files stored on the server. This is all I really need.

Also on that guy's site, you can use the vi clone or a command like *echo "Hello, sup yo." > file.txt* to create files. You can even *rm* them afterwards. I'm assuming that's why he's using php... but I don't know. My crappy shell would be strictly read-only. I had dreams of implementing some sort of *echo "you suck" >> file1.txt* type functionality for allowing comments, originally, though!

Still, the source is huge and uninviting for me, considering my general js n00bness. I'd rather not reverse-engineer this guy's entire project for my own meagre requirements. Considering that it'd be all read-only and not-at-all web2.0y, would I be able to do this without having to get into php?

---

### Post by fragos on 2009-02-17
You only need PHP if you're going to read and write files. Since you're after simplicity you probably won't need javascript either. You may find this helpful for HTML and CSS markup, [http://reference.sitepoint.com/](http://reference.sitepoint.com/). You can find a HowTo with step by step examples at [http://fragostech.com/HTML/HTML-1.html](http://fragostech.com/HTML/HTML-1.html).

---

