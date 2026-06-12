---
title: "East Asian Language Learning Programs"
date: 2007-01-13
forum: Education &amp; Science
---

### Post by blore123 on 2007-01-13
Hi,

I have found Kanatest in Games and I thinks it is really good.

Is there any other software for Ubuntu that does similar things, such as a Kanji Test or Chinese learning software (or even games...)

I would be very interested to know if there is ;)

---

### Post by blore123 on 2007-01-13
Three hours and no response - guess that's a not in a hurry, especially since I see no other forum threads on this kind of thing.

If not could you recommend a good programming language for me to write a program that does what Kanatest does? Not having my trusty VB in Linux, I feel I ought to move on up in the world and learn a proper language...

Thanks

---

### Post by anoir on 2007-01-14
Hi,

I found a program, langdrill, by quick search with synaptics. I'm not sure you like it or not, but it looks quite nice at least.

[lagdrill website]("http://storm.prohosting.com/borco/programming/langdrill.html")

A screenshot in flickr
[[IMG]http://farm1.static.flickr.com/134/357014559_807f94f927_o.png[/IMG]]("http://www.flickr.com/photos/67189739@N00/357014559/")

---

### Post by blore123 on 2007-01-14
Thanks! This is exactly what I need. :)

Is there anything like this that you know of for Chinese, and if so, does it also do Traditional Chinese as well as Simplified...

Thank you!

---

### Post by anoir on 2007-01-14
As for Chinese, synaptics suggests Hanzim.

[Website]("http://zakros.ucsd.edu/~arobert/hanzim.html") (currently not available)

This one is neither game nor drill. It just displays a Chinese character (Hanzi in Chinese) and information that helps users to memorize it (also Ping Ying).

A screenshot again (not beautiful with Tcl/Tk)
[[IMG]http://farm1.static.flickr.com/141/357155813_089e862d90.jpg[/IMG]]("http://www.flickr.com/photos/67189739@N00/357155813/")

Although langdrill does not have Chinese quizzes,  it seems pretty easy to write your own. Questions are stored in /usr/share/langdrill/ in utf-8 format (there are French and Swedish available).

---

### Post by blore123 on 2007-01-14
Great! Thanks :)

Is there anything like this ofr the Chese Languages, but more of a game? Or with a series of lesson-based challenges in the same way that the Japanese program above has?

I'll appreciate your feedback...

---

### Post by anoir on 2007-01-14
Nothing of that sort found. It might be better to start a thread in forums for language learners. Or use flash cards like

[jMemorize]("http://www.jmemorize.org/")
[pyFlashCards]("http://jewelmirror.com/")

Both are gpl'd and run on most platforms with Java and wxPython, respectively.

---

### Post by blore123 on 2007-01-14
Are these programs for Linux, or 3rd-party programs that just run seperately?

The other thing I'd like to know is how to open a catagory for Language Learners...

I think either a Moderator needs to do so or tell me how to do so - as I cannot find it in FAQ

---

### Post by blore123 on 2007-01-14
Actually, I would just like to say a special thanks to you for telling me about /usr/share/langdrill - would you be interested in any files I write (they'd probably be Simplified Chinese/Traditional Chinese/Japanese at the moment)?

Anyone who is, could you please let me have your name and email, and I'll send you anything I make.

---

### Post by anoir on 2007-01-14
I don't get what you mean by programs for Linux and by 3rd party programs.

According to apt-cache search, these programs are not available in my sources.list (very standard one with universe). So you have to install them by methods other than apt: in this case it is easy, because one is written in Java and the other in Python, assuming that you already have those environments.

I also do not know how to open a new category. It is better to consult moderators. If there are enough people interested in language learning, then those moderators will open one for us. Before that, talking about language under "Education & Science" seems appropriate. Or you can ask for help in local community, most of which have their own forums, listed in

[https://wiki.ubuntu.com/LoCoTeamList]("https://wiki.ubuntu.com/LoCoTeamList")

By the way, I meant non-Ubuntu forums by "forums for language learners", although it might be difficult to find people using OSS there.

---

### Post by anoir on 2007-01-14
You can upload files as attachments (up to 976.6 KB after compression)!

Does langdrill correctly render Chinese fonts? Should be okay as long as fonts are installed, because .drill files are written in utf-8, but I'm not sure.

I remember Chinese class I took in the first year of college was a nightmare...

P.S.
I found I misspelled "synaptic" as "synaptics" in earlier posts. That's a touchpad...

---

### Post by blore123 on 2007-01-14
Can you tell me how to enter Chinese Words/Japanese Kanji and Kana into gedit?

You mentioned UTF-8? And I Know how Windows IME works, just don't know how it's done in Linux.

Thanks.

:)

---

### Post by anoir on 2007-01-14
Use scim or uim (I'm using scim).

-Add languages you need in System->Administration->Language Support.
-Install scim-qtimm and im-switch
-im-swtich -s scim

This worked for me (you may need other packages like fonts and IMEs). Instruction is given in community documentation:

[https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM")

SCIM setting can be done through System->Preferences->SCIM Input Method Setup. After installation, you can use it like MS-IME (task tray & toolbar).

[[IMG]http://farm1.static.flickr.com/127/357381188_45247556a2.jpg[/IMG]]("http://www.flickr.com/photos/67189739@N00/357381188/")

---

### Post by blore123 on 2007-01-14
Great!

Now I have everything I need to write working .drill files for that first program you sent me info about. I *really* wish a Mod would read this thread and open up a Language Learning section in the forum topics list.

If you, or anyone else who reads this is interested in learning Chinese (Simplified/Traditional) or Japanese (yes, I know you are from Tokyo - so you don't need to, anoir...) - then like I said, write your Name/Email on here (if you don't wish to write it here, then just say so and I'll post and email account of mine to the forum)

:)

---

### Post by anoir on 2007-01-14
It would be great to start a thread about developing new langdrill questions for Chinese/Japanese (or any other languages). So far I found a few websites that refer to langdrill, like

[link]("http://chromakode.blogsome.com/2005/11/01/katakana-can-be-easy-the-open-source-way/")

but none has written his or her .drill file. Although the program works fine, it doesn't help users without questions. Having functional language learning softwares in OSS/Ubuntu sounds fantastic. If you manged to write decent .drill files, you might be able to ask developer/maintainer to include yours into distribution.

As you noticed, I live in Tokyo and obviously do not need Japanese lessons, but I can help you in Japanese. If you wrote one, I'll read through it to find anything wrong or unnatural.

[EDIT] And I'm pretty sure that there are tons of Chinese people who can help you.

---

### Post by blore123 on 2007-01-15
Thanks, any help with developing the software would be appreciated. Our dictionaries aren't always perfect, although they are not bad, and I do have a copy of Furigana, which as far as I understand is Japanese in origin anyway (I've another Japanese friend who recognised the name instantly).

As for Chinese, that's a real beast - since my Chinese friends either won't help me or just do so half-heartedly. So Chinese support would be great if you're out there!

Visited the website you placed in your last post, it great, and I have commented on it, as you'll see - but do you know a way of fixing the rather small font size in Langdrill? It isn't as good as Kanatest in that respect...

Thanks again :)

---

### Post by anoir on 2007-01-15
In my opinion, langdrill is suitable for little bit advanced learner who knows all hiragana/katakana and tries to memorize words and sentences. For hiragana/katakana, kanatest looks excellent. It makes sense to use two applications for two purposes.

There's no easy way to change font size of langdrill: it's a binary, not a script like python. With no preference/option within langdrill, we have to modify source in order to change size. Sadly, I'm not a programmer (okay I write programs for simulation/number crunching, but not for these kind of stuff).

After all, writing your own program is the only way to satisfy all demands, but still you can reuse questions you write later. If you like programming, I recommend python. The following program is written in Python. This one is for English learning (awful Verbal section of GRE), but should have similar structure.

[http://www.cs.utexas.edu/~arvindn/gretools/]("http://www.cs.utexas.edu/~arvindn/gretools/")

Not in repos.

---

### Post by blore123 on 2007-01-15
Actually, I feel the same way as you do, and as well as contacting a person in Taiwan using one of the links you gave me to cover the Taditional Chinese side of things, I have also emailed the developers of the Kana Test program for instructions on howto edit the Kana Test program to add Kanji/Chinese to it, since I know it uses fonts now - and not images.

If anyone else can help - I would appreciate knowing how Kana Test works and if possible, how to edit it.

Thanks

---

### Post by anoir on 2007-01-15
Kanji has multiple pronunciations both in Japanese and Chinese. So the method Kanatest employs won't work for it.

As for Kanatest, its questions are hard coded in /kanatest-0.4.0/src/test.c. It might be troublesome to change them.

---

### Post by blore123 on 2007-01-15
I have v0.3.6 and I caanot find the files you mention - I can only find pngs so I guess I need to upgrade it!

:-?

---

### Post by blore123 on 2007-01-15
Ok, upgraded my copy to 0.4 and found said files...

This looks like it is begging for some overhauling!

I am of the opinion that you do not quite understand my idea on this. Instead of user types the romanji of a *Kanji* that is displayed, they type the meaning of the word, or better still, to remove ambiguity, it gives a list and they merely type the number from that list.

This method makes Chinese actually possible since learning to type for Chinese is as hard as learning Chinese itself if you have an English keyboard without the characters printed on it!

Thanks for the file information, I'll be plotting how to write the thing in C.

---

### Post by anoir on 2007-01-15
Found here:
[http://freshmeat.net/projects/kanatest/]("http://freshmeat.net/projects/kanatest/")

It's amazing that kanatest was laste updated on Jan. 4th 2007!

---

### Post by blore123 on 2007-01-15
It is, makes you wonder if they'll email me back partway through me developing improvement to tell me they have made them!

I've also emailed another Japanese friend I have who uses Fedora for advice. I'm starting to wonder which way this is going...

---

### Post by anoir on 2007-01-15
Good work!

Since the developers are active, there is a good prospect that they can add some features if data/questions are provided.

And now I understand what you want to do. Even though Kanjis may have several meanings, each Kanji has its vague idea. By getting familiar with these ideas, you may at least guess what words or sentences mean. Actually, this can be an excellent start point for further study.

---

### Post by blore123 on 2007-01-15
Glad you like it. I started on Tuttle Kanji cards, so I know it works, and the nature of kanatest makes it fun too. I think I'll need more programming skill - but I'm a fast learner and this is definately worth it.

Plus I seem to have a lot of support amongst opensource users!

---

### Post by ryukent on 2007-01-16
Hi,  Just thought I could lend a hand. I'm a Brit living in Tokyo and am in the process of developing cross platform (Java) English-Japanese language learning software similar to the one's you've mentioned. If you have any good ideas and specifically data that I can use within the program (like word sets) etc... I would be most interested. Writing the engine is no problem, it's getting those thousands of words in that takes time.

---

### Post by blore123 on 2007-01-16
Tell you what, I reckon you can put this together faster than me and we can have a customised program if we work together.

If you like the idea, add [email]blore@hotmail.com[/email] to your MSN buddies list (I have Gaim and MSN on Ubuntu, so we can exchange files and things, but I should also be able to sort out ftp space for us to share if necessary too (MSN hates .exe files)

If you show me how to input the data - I have setup Ubuntu with lots of language support with help from anoir, so I'll spend a lot of time putting sets of Kanji and Kana into the thing. I was going to start with  The six grades of Government-Approved Kanji (Jouyou) and then move out to include some words from Nelson that are useful in everyday life.

A common shortfalling of many Kanji-teaching programs is they lack words comprising more than one Kanji at the top-end of difficulty. This means that the user can only read Japanese word with one Kanji in and gets confused at everything else. (I mean if we learnt 'butter' and 'fly' and a child, you cannot expect us to know that 'Butterfly' has nothing to do with butter!)

If you want help with writing the program, that'll take me longer, as I was going to mod the Kana test program - but if you can write a program, that would be awesome (I have done this in VB, but not C or C++ before). I would say if you're using Java, resist the urge to use graphics - stick to fonts for the Kanji and Kana, I found it works a treat. If you need me to supply those with the data I send just say so and I will send you all I can.

I look forward to working with you if you are willing!

Thanks.

---

### Post by ryukent on 2007-01-16
I know exactly what you mean with single Kanji. This is because the programs are targeting you to learn the Kanji on it's own. But t he problem is, in a real Japanese environment, it's far better to take a vocabulary focused approach. The system that I've got (which I use myself) and has proved quite effective, focuses on words and has an optional output of Kanji, or Kanji + Hiragana.

Learning all the words that go with a Kanji at the same time isn't necessarily a good idea as some will be far more complex than others. It's better to be learning vocabulary at the correct level of Japanese that suits your ability and try and pick up the Kanji's that go with them as you go along. Primarily, you will need to know the word first as in conversation, you don't have the luxury of seeing Kanji to help you. Once you understand the word and it's Kana pronunciation, then you can move on to the Kanji.

For this reason I have taken to a English / Hiragana / Kanji structure with my vocab sets working progressively from one side to the other with the optional ability to display what the user is targeting their learning to. Of course, it is also important to learn eng>jap as well as jap<eng.

I should have a good beta model within a couple of weeks. If you have any sets of data in the "English, Hiragana, Kanji" table structure that would be great. As would any feedback on my designs. I'll send you what I've got as soon as I've smoothed the edges somewhat.

---

### Post by anoir on 2007-01-17
I agree with ryukent: vocabulary focused approach will work better. Show words which contain Kanji and Hiragana with ruby and then let users to choose a correct meaning and vice versa. It would be even better if the program has options to hide Kanji or ruby to better suit one's need. In conversation you cannot see Kanji and all the words are not separated clearly.

Japanese people start to memorize Kanji at the age of 7 and expand their memory by 100-200 every year for 6 years of elementary school. However, children surely know meanings of words they learn, if they are written without Kanji. For non-natives learning both at the same time seems easier and faster.

A feature to provide an example sentence to each word will further benefit users.

---

### Post by blore123 on 2007-01-17
This is really aimed at you, ryukent...

Do you need the table in any special format? (such as comma delimited)

Once I know how you want it, I will start posting data here and also get an ftp site set up so we can freely exchange much more data. I'll need an email address to send you the userID and Password for that account. I'll send you the six grades of Jouyou and also some catagorised lists such as numbers, days of the week etc...

For the record, both of you, I took the Kanji-only approach with two effects:

1. I become good at reading Japanese, but could barely converse beyongd the very most basic sentances.

2. My Japanese friend here in the UK called me 'crazy' for learning them before Kana!

---

### Post by blore123 on 2007-01-18
I have received an email reply from Tomek (the writer of Kanatest) and apparently Kanatest cannot be modded to do other character sets. Having examined the code, I can see why. You'd need to re-write most of the program just to change the tests.

Tomek says it would be possible to write a Kanjitest program at a later date as a fork, but really needs some free time to do this. Also, as with all these programs, some data is needed (I have volunteered to help there if I can).

Just thought I'd keep you guys upto date...

---

### Post by blore123 on 2007-01-19
Another update:

I bought a Chinese Dictionary yesterday. My other one was only English to Chinese (although that's still quite useful as it's big and has a useful section of categorized words), it does at least mean I can check the quality of the data I'm sending you guys once the Japanese version of this program is done.

I have also seen a *huge* Japanese dictionary, but won't get it until Nelson cannot cope anymore (that covers over 3,000 Kanji).

Ryukent, if you could let me know how you want that data, as I'm itching to get a good start on it, rather than keeping you waiting...

---

### Post by ryukent on 2007-01-21
Yeah, sorry for the late reply. I've been in Hakone this weekend bathing in hot springs. Basically, at the moment my system read vocab data in the format "English/Hiragan/Kanji". For example:

"Word, language, speech", "&#12371;&#12392;&#12400;", "&#35328;&#33865;"

I have taken to using multiple english words to describe a single japanese one if it is required as there are many that don't have a direct translation. Also, for Katakana words, I've kept the format strict, used a hiragana expression in the hiragana field and just put katakana for kanji. Where there is some debate on the meaning, I've chosen Jim Breens JDIC (online) as a reference. My data sets are currently in spread sheets, but my system can read CSV (comma separated variable) files, mySQL and Apache Derby databases. I could add extra support, but I think these 3 are sufficient.

If you'd like, I'll send you some of my data sets.

All the best,

Ryu

---

### Post by blore123 on 2007-01-22
Hi,

No worries about the weekend, I wasn't there either, I was at the University for 36hrs.

If you want to send any data sets, then send them to [EMAIL="simon.david.blore@btinternet.com"]simon.david.blore@btinternet.com[/EMAIL]  - I'll get back to you when I've reviewed these and have created anything that's not yet been done. (This won't take too long for the first few sets).

Thanks again for your help...

---

### Post by FrankVdb on 2007-01-26
I'm also in the process of learning Chinese and I have many, many dictionaries.

However, although I have a few good ones, it takes quite some time to look up characters. 

Two weeks ago, I "stumbled" onto an electronic dictionary that allows me to look up characters in a matter of seconds. It's called "Wakan" and was written by a Czech guy:
[http://wakan.manga.cz/](http://wakan.manga.cz/)

It may be open source, I'm not sure, but the underlying dictionary (CEDICT) certainly is.

Unfortunately, it has been written for Windows and the guy has no intention to port it to Linux... It would be great if someone could write a similarly good interface for Linux based on that same open dictionary. I'm very interested in learning Python but currently time is not on my side. I have very few hobbies, but they take all of my spare time...

As far as SCIM and SKIM are concerned, my experiences have been very bad with them (under both Dapper and Edgy).

---

### Post by anoir on 2007-01-27
This program, wakan, is really amazing, but it is just free as in beer, not open source as of now(only free for non-commercial use and no download link for source files).

I tried to run it with only partial success (fonts on menus are broken):

[[IMG]http://farm1.static.flickr.com/174/370569253_3c2db4373a.jpg[/IMG]]("http://www.flickr.com/photos/67189739@N00/370569253/")

It seems, however, not so difficult to fix this through some tweaks (no time to do further research right now, though).

I'm using scim-anthy in dapper & edgy for all the work without any trouble. I admit it is not as efficient as other commercial IMEs available in market. It would be painful to write serious documents.

[UPDATE]
There is a discussion to make WaKan project open source:
[http://wakan.manga.cz/forum/viewtopic.php?t=415]("http://wakan.manga.cz/forum/viewtopic.php?t=415")

It is confirmed that WaKan runs successfully:
[http://appdb.winehq.org/appview.php?iVersionId=5585]("http://appdb.winehq.org/appview.php?iVersionId=5585")

[UPDATE2]
Now it seems working rather well:

[[IMG]http://farm1.static.flickr.com/132/370603702_364014e74b.jpg[/IMG]]("http://www.flickr.com/photos/67189739@N00/370603702/")

---

### Post by blore123 on 2007-01-27
Hi,

You're right, it does look amazing.

I have been compiling these lists for Japanese for ages now, and then when I have done enough, I get to start again and do Chinese!

I can say this though, if using dictionaries is slow, you need to learn the radicals as well as you can - and how to spot which is the main radical in a word. That'll find you the entry in Chinese dictionaries the fastest. (If you ever do Japanese, just get Nelson, all you need is the ability to count, and it's really easy and fast to get used to as well :))

Back to work...

---

### Post by anoir on 2007-02-07
Hello.

You guys are still around? This week I'm finally freed from tons of tasks and got a good amount of time. I made up mind to learn python seriously. As everybody knows, the best way to learn a language is to write a program with it: so I started writing my own testing software for Japanese (or any other languages in unicode, for which I have no idea on even how to input).

Yesterday I started writing one. It's very simple yet: it just displays one word and five possible answers, from which an user choose the correct one, repeatedly, but it is already working. I'll add other functionalities and user interfaces later.

Attached is the tar.gz file which contains all the necessary files. It runs by python KanjiTest.py. You need pygtk as a dependency.

Data file is designed to be simple. It's a csv in utf-8: 1st column for words, 2nd column for pronounciation, and the all the subsequent columns for English definitions, one cell for one definition. I treat each definition separated for later use.

I appreciate it if you can provide some data sets. Don't need to care about format. I'll do conversion if needed. I'm really enjoying writing programming now (very different from number crunching coding).

---

### Post by blore123 on 2007-02-09
Hi,

Yeah, I'm around, and painfully trying to copy and verify all 80 of the first grade Kanji, plaus a few everyday use words too (days of the week etc)

Sorry not to post much recently, but like you said: up to my eyes in it.

I'll get you the files very shortly.

Thanks :)

---

### Post by ryukent on 2007-02-11
I've been entering data too.... hope we can pool our resources. My Java program is nearly ready. I hope to post it here by the end of the week.

---

### Post by blore123 on 2007-02-12
Hi guys,

After some time entering, and then cross-checking these grade one Kanji so as to make sure everything was stright, I've got you the file. If you want it in .csv format, just rename it, or I'll email you a copy if you ask me.

Tote this isn't the only one I'm doing (doing days of the week, dates etc and other useful words eventually).

Now to write some XML files... (gasps)

Hope these are useful.

---

### Post by ryukent on 2007-02-15
Good work blore!

Right, I finally have a stable release of my program. It is available at:

[http://www.japanese.ryukent.co.uk/](http://www.japanese.ryukent.co.uk/)

Please try it out and give me any feedback. Note that the zip file includes some sample data. This is very much a first version so I'm sure there are many revisions needed. Please note also that you need to have Java 1.6 installed. There are many guides on how to do that for ubuntu.

Cheers guys... I look forward to my next release.

---

### Post by blore123 on 2007-02-19
I have to say, I cannot figure out how to get this Java 1.6 running on my computer at all. I appear to end up with a .bin file and never have permission to even run it, despite using superuser in terminal to do so.

Can you give me a hand here? I checked Synaptic, but only found a Java 1.4 file, which is worse than what you say I already have(?!)

Any help at all would be appreciated...

---

### Post by ryukent on 2007-02-19
Oh yeah, it's a little annoying to have to install Java before ubuntu get round to including it in their packs. Right, basically what you wanna do is right hand click on the file in File Browser and go to the permissions tab. There you will find "Allow executing file as a program". Make sure this is switched on. Open a console window so you can see the output and enter 
```
"sudo ./filenamehere"
```
Where filenamehere is the bin you downloaded. That should pop you up with a couple of questions on agreeing to their licence and there you go.

Hmm... I wish the Ubuntu people would include Java 1.6 in the repos... would make things so much easier.

---

### Post by ryukent on 2007-02-19
Oh yeah, sorry one last thing: You'll need to add these following lines to your .bashrc file in your home directory, otherwise the previous version of java will still be used:

export JAVA_HOME="/opt/jdk1.6.0"
export PATH="$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH"

Note that /opt/jdk1.6.0 is where I've got java installed, it will be different for you. And regarding the above post, you might have to try 

sudo sh ./filename 

instead of what I wrote, but permissions apply the same.

Finally, if double clicking on the file doesn't work, you might need to execute it using

java -jar TangoBlaster.jar

I appreciate this is all a little complicated, but with a correctly installed version of Java, it should just run on double click... obviously I'm not responsible for making Java easy to install on ubuntu.

---

### Post by blore123 on 2007-02-20
I also wish they'd include tangoblaster with all dependencies as a package as soon as it is at v1.x stage - hint, hint, wink, nudge, etc...

---

### Post by blore123 on 2007-02-20
I'll tell you what, we SERIOUSLY need to get this in an online repository, even if we have to mark it as unstable or something, as putting it together and installing all these extras is really exhaustive and may put less tenacious users off.

---

### Post by blore123 on 2007-02-20
Ok, so tried to run it after finally sorting the whole list of things as described, here's what my terminal spat at me:

simon@LinuxOne:~/Desktop/TangoBlasterDist$ java -jar TangoBlaster.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass2(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:719)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:160)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:254)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
simon@LinuxOne:~/Desktop/TangoBlasterDist$ 

I'm dying to try this program out, do you have any idea what's up?

---

### Post by blore123 on 2007-02-20
Panic over for the program, it just needed about 3 restarts (and I'd used the command ...JDK1.6.0 in my bash.rc file whereas I only downloaded the end-user JRE1.6.0 (what a fool I felt for not spotting that)

It runs with one error:

Error -- java.io.FileNotFoundException: settings.config (No such file or directory)

Don't know if it is bad, but it appears to not affect the program so far.

Now the program itself has no font's working in it! The new Sun Microsystems file fontconfig.properties.src has been inserted as previously described, but alas nothing but boxes appear where Kanji and Kana should (English still ok)!

Like I said, this program will need to be packaged in Synaptic for others asap, I'm going through hell getting it to work.

Sorry about the last problem, it was clearly upset with version of Java, just could not figure why it hadn't adopted my 1.6.0 code, but that's sorted now :)

---

### Post by blore123 on 2007-02-20
Once again, after some tinkering with my computer, and getting used to the program, I have finally fixed it.

The program is *really* good, but as you say, needs absolutely bombarding with data sets, as frankly the program needs all of Nelson loading into it and even then you'd still not speak perfect Japanese, you just be good at working out what it said. I do have a copy of Nelson, but obviously 30,000 words aren't about to appear on this forum, as I don't have a lifetime to do this, if enough people did have a bit of time, we could though.

I'd advise you to press for a v1.x of TangoBlaster so it can be placed on Synaptic with it's dependencies and configurations behind it, so less patient Ubuntu-ers can enjoy it too. You mention that you use Fedora in your setup instructions - with this much technical knowledge, I can see why.

As for Data, please tell me what you want, and I'll commit 30-60mins a day feeding this program with those CSVs - I believe it can be very powerful if we put the work in.

---

### Post by ryukent on 2007-02-21
Thanks blore, glad you managed to get it working in the end.... as far as the fonts were concerned.... the file error you got is normal the first time, because it will just use default font settings until you set your own and it will write this file and read it next time you run the program.

As far as not being able to read the fonts, well you could have selected them individually in the settings window. My problem is that there are no good set of Japanese fonts that all systems will have. For this reason, users are always going to have to do a small amount of setting up. Actually, you didn't need to change the font.properties file.... it will read fonts directly into the program (though it does use more memory that way).

I think the solution to most of these issues is to re write this as a Linux only app using SWT and target at Java 1.5. I just wanted to make use of some of Java 1.6 features, but I guess it's still gonna be too hard for people to have to set up Java 1.6 until Ubuntu have sorted out a repository package to do that.

Failing that, I might just abandon Java and opt for C instead, but that itself brings up a whole load of new problems. The goal is to make this as platform independent as possible.... actually, it doesn't work in windows yet, but I still need some tinkering. As far as I can see, Java is still the best way of making it easy for everyone to install. As long as they can get Java on their system, it should work fine. In windows this is a matter of double clicking on the self installing java package. If I'm gonna redo this in C, I'll have to compile loads of different versions and cater for different linux dists.... I'm not sure I want to do that.

My current project is also to get a good web based version running too. I'm gonna try and use AJAX and have this client version and the web based version able to connect to the same online database that I can store a master list of vocab on. That way, when I update it, the client and web based version will both see the updates at the same time.

On what vocab to do... well, I have a current database of 22,000 of the most commonly used Japanese words, but...... there's no kind of ordering of importance or difficulty. I've gone through some of my old textbooks and copied some stuff from there, but again, there's a problem that most of the books I've got are kind of intermediate/advanced ish level and they tend to mix very specific stuff in with simple words too.

If you were able to come up with some sets of words that were aimed at beginners and that were roughly all at the same level within each set, I think it would really help people who want to progress at a steady pace.

Of course I see this as a community based community aimed project and I look forward to adding full acknowledgements to anyone who has helped within the program.

Thoughts and suggestions are very welcome!

---

### Post by ryukent on 2007-02-21
Well, I've found the solution for an easy way to install java:

[http://tuxicity.wordpress.com/2006/12/07/installing-jdk-6-rc-mustang-in-ubuntu-edgy/](http://tuxicity.wordpress.com/2006/12/07/installing-jdk-6-rc-mustang-in-ubuntu-edgy/)

It's a repository based easy way to install Java 1.6 with no faffing about with environment variables. I think this solves pretty much all the problems. As far as the fonts are concerned, I'll just write a more in depth instruction set including a facility to download a font.properties from my page.

---

### Post by blore123 on 2007-02-22
Ok, so we have Java 1.6 sorted - great. If you bust a gut like I did rewriting the properties file than apart from breach of a certain licence agreement, you actually save some memory OR just use the repo - so it's win-win really, you can have memory or simplicity.

Don't abandon Java, it is a good system and a good program, and hey, if this takes off, it'll work online even, and on M$ OS's that I wouldn't waste my spit on. (Incase you want to go that way too)

I have Japanese for College Students, and it's a devil of a book for springing new vocab in and not explaining stuff properly. In fact I reckon the web and a copy of Nelson are the best (Nelson to verify the web stuff). Let others do the work, since you cannot copyright a language.

I'll see what I can find, can you retain the data files' names I supply - as that will allow loading them into TangoBlaster easily, without wondering what each CSV contains (or having to stick another post-it next to your machine!)

Thanks...

---

### Post by ryukent on 2007-02-23
Right, been busy, finished the next version. This one comes with a full EDICT derived database of around 22,000 words. I've fixed the problem with windows and it's dodgy Japanese character set. Now everything should run smoothly in UTF-8 unicode. Cool.... ahhm... also made running it easier by adding a shell script. There's a nice GTK theme too so it will look all linuxish when run in Linux. As far as your data's concerned, I think it's best to have names that don't reflect the original source in order not to anger publishers. You're right, you can't copyright a language, but there might be something about copyrighting a list if supplied in the same order or grouping. For this reason, it might be sensible for us to re-order them and give the sets standard names too. What do you think?

---

### Post by ryukent on 2007-02-23
The aforementioned new version of Tango Blaster is now available at [http://www.japanese.ryukent.co.uk/TangoBlaster.html](http://www.japanese.ryukent.co.uk/TangoBlaster.html)

---

### Post by blore123 on 2007-02-23
It is ok, do not worry, I wasn't going to raid a site wholesale, just look for lists of common vocab and use them as a basis for a .csv - that's all.

It looks good the new version does, I'll give it a spin soon.

---

### Post by blore123 on 2007-02-25
Hi,

I've encountered a couple of things I need help with.

1. Not so important, but I noticed root cannot run TangoBlaster as it appears to be launching JRE1.5 still, is this ok, and can it be fixed?

2. More importantly, I was under the understanding that TangoBlaster would be able to take a Chinese data set if the csv was written in the same format. First, I need to make it clear from trying, that all contributors MUST make .csv files UTF-encoded, as other methods are absolutely horrible to use. Secondly, when run, a Chinese set only shows the words that have Japanese fonts. Can you tell me how to add Traditional AND Simplified Chinese ones to this program, and I would guess a few out there may appreciate Korean too ;)

Hope the feedback helps, and thanks...

---

### Post by ryukent on 2007-02-26
OK,

1 - If you have your Java path set up in your user's bashrc script, then it won't run when you're root because it is associated with your user only. The root script will run instead. This is when happens when you set up java on a per user basis. If you installed it from the repository (that link I posted) then it should effect the whole system (note it will then be overruled by your user script). Basically, Sun will make a final release of Java next month and then we should have a nice repository packaged file that will install it all automatically and none of this nonsense. I've written to them regarding why they've made a full Java 1.6 release but not backed it up properly and have had no reply. It seems I've written this in a version of Java that's not been fully released yet. This should all be sorted in a month or so.

2. There's actually no reason why it can't run Chinese files. The wonder of Unicode (in this case UTF-8) is that it supports all languages. The problem I suspect is that you've not got fonts set up correctly. Pre-empting this, I built in that feature to specify a TTF font from a file. So you have 3 options (in order of simplicity):
a) Point directly to a Chinese supporting TTF font file from within Tango Blaster
b) Select a Chinese supporting font file from the drop down list of installed system fonts...
c) Make sure your java font properties file is configured for Chinese. I thought it would be defaultly, but obviously not.

Hmm... yesterday I installed openSUSE. I really loved the way that Japanese just worked straight away with no faffing about. Java was installed automatically with full Japanese fonts too (though it was 1.5).  I am starting to think Ubuntu is a little flakey in some areas.

---

### Post by blore123 on 2007-02-26
Just for my benefit as much as anyone who's following this, which fonts contain support for Chinese (Simplified), Chinese (Traditional) and Korean words and syllable-characters where necessary (these are the kana-equivalents such as those seen in Traditional Chinese)?

---

### Post by blore123 on 2007-02-26
Ok, I have found that Googling for Chinese Ubuntu Fonts tends to get me where I want. I'm using a system font now called AR PL SungtiL GB and it has Japanese and Chinese well covered, even Taiwanese :)

Please see my screenshot below to see what the first TangoBlaster is now able to do!

Obviously, the second TangoBlaster probably does more, but getting this far is great news for getting the program on future distros of Linux as a whole...

---

### Post by blore123 on 2007-02-28
Ok, here's something new...

I've not fully verified this file yet, but if it is right, and TangoBlaster does not mind having csv data with only TWO columns of data (hopefully it then leaves third field empty), then we have TangoBlaster able to run Gyoyu for Traditional Chinese in a similar way that Kanatest runs for Japanese. You will need a Traditional Chinese - supporting application font for this to not just spit boxes at you either way (see previous posts).

Ryukent, can you tell me does the TangoBlaster program test you more frequently on items you mark in the test as 'incorrect'? If not, can this be added, as it is one of the best features of Kanatest. It forces you to tighten up your worst areas, although it is a little sensitive to a single, freak error if you ask me...

I'll test this tomorrow - enjoy!

---

### Post by blore123 on 2007-03-01
Ok, I tested it - it works fine. The kanji window shws nothing even if called, so no problems there. Few other things I found were:

1. You don't need to use .csv files - as long as the file is set out in this format:

"English"  "Kana"  "Kanji"
"English"  "Kana"  "Kanji"
etc...

then you have nothing to stop you loading in a .txt! This is handy as .txt files are much easier to handle, especially with Windows having the better support for foreign language input in England.

2. There's an option called 'chunks' that I don't understand. What is this? My guess is a reference to spaces found in some data sets, creating smaller chunks of data within a .csv file (or .txt) - am I right?

3. Statistics. These would be useful if added. Perhaps they should also league table the user's most incorrect words as well, so they can learn them more thoroughly. It is another cool thing Kanatest had that we do not yet. We have the chance to make this a little better too.

Just my $0.02-worth... :)

---

### Post by blore123 on 2007-03-01
Ok, I get chunks now, it is a way of breaking down large data sets without manual chopping. That's a good idea too :)

The stats are definitely the most important improvement that can be made now, you *could* go for a multi-choice option should the user want it, but you'd need to add multiple possible answers to each .csv - so it has its upside and it also has its problems too. Still, my approach would be to place the option there and then default it to off. This way we get the best of both worlds!

Does the random option work yet, I cannot see any change?

Hope these ideas help you.

---

### Post by blore123 on 2007-03-01
Right, sorry I missed the whole chunking explanation as posted on your website! Felt a fool when I found it.

The new TangoBlaster 0.7 has a couple of tweaks it needs:

0. Just like to say I'm not saying it is bad, just trying to help iron-out potential issues. The program is insanely easy to install, you also retain all previous fonts, so when my already open terminal window simply needed me to repeat the java command - I was pleasantly surprised, thanks :)

1. The DB is great so far a raw quantity of data is concerned, but I feel is somewhat useless beyond that. How can a person recall a chunk done after a restart of the computer? They might as well read Nelson, at least it is in the same (radical and stroke) order each time. It think it has to be impossible for average Joe public to use this method of learning.

2. Rather disturbing this one - I ran TangoBlaster 0.7 from the DB mode and I use a UXGA (21") monitor for Linux - in case anyone does not know what resolution UXGA is, it is 1600x1200 pixels. You will not get much bigger than this, is my point. I ran very quickly into this problem (see screenshot attached). No data sets can exceed 1600 pixels on the English line, it is just unusable visually - I suggest word-wrap or auto fontsize adjustment if this happens in any given item. You should take a look at this screenshot, it really is unbelievable!

3. Still no stats, after you complete a set or a chunk, and data is still displayed in a strict order even if you select 'Random'.

4. TangoBlaster now does an annoying thing on startup: it maximises. Ok if you have a tiny screen and are used to one-screen-to-one-task usage, but like I said, I use a giant screen, and it just fills it with grey. The old version did not, so I am unsure why this is necessary...

5. Not really a criticism - but a warning to users: watch the .csv - you *must* export one before importing another, or it just appears to mix the two together, and the effects are very dire. I was running my Chinese (TW) set after using the DB and got Guoyu in the entries from the DB! If in doubt, keep terminal open and just close TangoBlaster completely, then repeat the command in terminal and all data is flushed for you!

Hope that's not too harsh, it is not meant to be...

Thanks for the new version.

---

### Post by FaceLeg on 2007-03-05
> **blore123 said:**
> Actually, I would just like to say a special thanks to you for telling me about /usr/share/langdrill - would you be interested in any files I write (they'd probably be Simplified Chinese/Traditional Chinese/Japanese at the moment)?

Anyone who is, could you please let me have your name and email, and I'll send you anything I make.

I'd be interested - also have you been able to get Hanzim working?

I am a total noob...

I can't seem to follow the instructions on the Hanzim site.

I have installed it with the package manager, but I have no idea where it went...

:confused:

Slightly less noob now, I figured it out.

It isn't that great though, I don't really understand the point of it.
Back to writing the characters out over and over again.

I would offer to help you guys with your program, but I am bogged down with uni work at the moment - Chinese is difficult to keep up with, as I am sure you will understand.

If you need a tester, add me to MSN.

Thanks,  

Mike.

---

### Post by blore123 on 2007-03-05
Hi,

I have added you to my MSN account, so I can have a chat with you if you're ever online.

I do agree a little about Hanzim, I got it working but found it not as good as other programs availe at that time (much less TangoBlaster which RyuKent is doing such a great job on). Since it can really be taught to do anything, I feel that's the best thing you can do to help - just follow RyuKent's instructions on his site and get TangoBlaster working. As he says, you need Java 1.6 (Download the JRE 6 or JDK 6 from Sun at the link he gives) and also you need to have a font that supports all the languages you want it to do (usually just one!) The 'test font' option in TangoBaster is a very smart idea for this, but I just ended up changing my system fonts, it makes Ubuntu look better and there's half the setup done very quickly. The rest is simple, just open a terminal screen and goto the folder you have TangoBlaster in and type:

java -jar TangoBlaster.jar

Most of the errors you get are meaningless to me, and the program works anyway, as long as you do what RyuKent has said (probably for a reason, as I learnt the hard way :))

After you get it working, just ask for things, like vocab - if you haven't the time, at least what I write can be aimed at what you actually want, instead of what I *think* you want.

If you are trying to learn Traditional Chinese, look out for Guoyu, I can get you font's that will allow you to display those in the place of Kana in TangoBlaster...

Hope this helps you :)

---

### Post by ryukent on 2007-03-05
Right, after a short period away, I'm back on the development case again. Good point about the maximising, I can see how that would be annoying. I added it because I wanted to concentrate on what I was looking at, but I shall make it optional.

The random feature does work. It shuffles the order that the words are displayed.

As you are using this for chinese too, I think I shall change the heading "&#12402;&#12425;&#12364;&#12394;" to reading.

I've noticed you're still using the java command. You don't need to do that any more. Just type "./tangoblaster" while in the correct directory and it should load with the Linux Gnome skin enabled.

Database entries can be saved as CSV files if you want  to go back to the same set later.

Yes I know some of the english explanations are too long. Not sure about what we should do about this yet. I don't really want to make the English field multiline as it would become too big. Maybe a popup button for a full explanation... what do you think?

For the stats.... great idea. I was thinking along those lines too. I'm going to add a pass per complete ratio which should allow you to see how quickly you are absorbing them. Then we could have totals too.

Adding additional datasets from CSVs includes what you already have loaded. Hit clear set to remove existing entries. This means you can build a set from more than one list.

As far as showing the ones that you get wrong more often... yes it does this. It will continue to cycle every word you get wrong until you get the all right in each set. I use it like this:

1. Load a dataset you want to learn or create one from the database and save it as CSV if you want to go back to it later.

2. Run through it using chunks of size 10. This will cause you to learn each word at a reasonable rate.

3. Reload the same dataset from the file you made, turn on random (to change the order) and run through the file with no chunks. The first pass will eliminate any words you know straight away. At this point, you can wither save the set again so that you have a list of words you know you don't know and need to work on, or simply cycle through the remaining words which are just the ones you got wrong. In next pass you should have remembered some of the words from last time. Keep going until you've got them all right. It removes correct ones from the list and shows incorrect ones again and again.

This is the most efficient way you can learn. I cannot possibly think of any feasibly more efficient way of learning because you keep looking at words you've got wrong until you don't get them wrong any more. If anyone can improve this method the let me know, but I believe this is the best spent usage of time.

---

### Post by trippinnik on 2007-03-06
Hi Great work!  Looks good.  I am can't get it to work fully.  I just got your program from your site.  I can get it to run by opening the Jar with java6, but your script gives me this error:
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file
        at java.lang.ClassLoader.defineClass2(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:719)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:160)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:254)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
When i do run from the jar, it says there is no data?  I don't have any csv made... Do i need to import one?  How can just learn random Kanji and vocab?  Can i get some csv files from someone else?  Thanks, Nik

---

### Post by trippinnik on 2007-03-06
Oh, my mistake.  I&#12288;had installed java6 but it wasn't set as the default....
Good stuff.  Is there any community for adding kind of story/pictoral discriptions for kanji?  I Have seen a few books that do this and it seems to help with memorizing them.  I know that would be a pretty major feature to add.. but if there's already some kind of database it could be added when you hit the show button.
Anyway, those are just my thoughts, but it's already my favorite way to study kanji on the train!  Thanks a ton.

---

### Post by ryukent on 2007-03-07
Regarding the previous link I posted...well it won't work any more as I've changed my site around a bit. [http://www.japanese.ryukent.co.uk](http://www.japanese.ryukent.co.uk) will always work.

---

### Post by ryukent on 2007-03-07
Hey... Blore, seeing as you asked so nicely... I've added some of your requests. Tango Blaster 0.7.2 is now available and includes:

Statistics
Maximisation option (in config)
Popups

To get the popups, you click on the label (e.g. English). For now I think this is the best remedy for entries that are too long. In the long run, maybe not, but still thinking about what to do with this.

It's available in the usual place. See link above.

---

### Post by FaceLeg on 2007-03-08
> **blore123 said:**
> Hi,

I have added you to my MSN account, so I can have a chat with you if you're ever online.

java -jar TangoBlaster.jar

Most of the errors you get are meaningless to me, and the program works anyway, as long as you do what RyuKent has said (probably for a reason, as I learnt the hard way :))

After you get it working, just ask for things, like vocab - if you haven't the time, at least what I write can be aimed at what you actually want, instead of what I *think* you want.

If you are trying to learn Traditional Chinese, look out for Guoyu, I can get you font's that will allow you to display those in the place of Kana in TangoBlaster...

Hope this helps you :)

I broke my Ubuntu (AGAIN), have just finished reinstalling...

I am installing aMSN now, hope to see you online.

I have JDK 6, main reason for moving to Linux (other than disdain for MS...) was to use Eclipse, since all my COMP papers are taught using it.

Over the summer (Nov-Feb here) I wrote a flash card program in .NET for The New Practical Chinese Reader Vol1 & 2.
This is the Text that many American, Australian, Canadian, European and New Zealand Universities use.  Unfortunately my workload is such that I do not have the time to write new vocab files for this project.  On the off chance that it would be helpful however, I have attached a text file containing the entries (in the format read by my program) here.

I have some more, written for The New Practical Chinese Reader Vol. 2 - but they are locked in the installer...that was made for windows.

Here they are:

---

### Post by FaceLeg on 2007-03-08
6-10

---

### Post by FaceLeg on 2007-03-08
...I seem to have deleted the files I made for Vol. 2.

The format is the same, the text begins from chpt 15 and carries on from there.

I still have not installed Tango, it is next on the list.

I know I have a copy of Vol.2 files chpt 15- 18? somewhere...

---

### Post by blore123 on 2007-03-08
Firstly, thanks for the data, what kind of Chinese is it in? Sorry, I cannot use in until I switch HDDs over! But I'd like to, so I ought to know...

Second, did you know that TangoBlaster does not need .csv files? It'll use these .txt files as is provided the data is laid out correctly. Just drop the .csv filter on Importing the set and select your .txt file, and it works fine! This is doubly good as Windows appears to have the better writing tools in the shape of the IME and the Soft Keyboard.

---

### Post by blore123 on 2007-03-08
Oh, Ryukent, sorry to not reply in that, since I just spotted your post in amongst all those data sets...

Thatnks, since you've done that, I'll go and check those out for you tonight, a friend has put together a nice big Chinese (TW) data set for me, so I can post that for you if you wish. I think what we'll have to do is seperate them out soon. Instead of posting many languages and randomly sized sets onto this thread. Perhaps I'll work on summaries and stuff once I've finished these blasted Japanese numbers (I'm upto about 60, but want to also include hundreds and things as they get irregular up at that area).

Thanks for all of your efforts...

:)

---

### Post by FaceLeg on 2007-03-08
> **blore123 said:**
> Firstly, thanks for the data, what kind of Chinese is it in? Sorry, I cannot use in until I switch HDDs over! But I'd like to, so I ought to know...

Second, did you know that TangoBlaster does not need .csv files? It'll use these .txt files as is provided the data is laid out correctly. Just drop the .csv filter on Importing the set and select your .txt file, and it works fine! This is doubly good as Windows appears to have the better writing tools in the shape of the IME and the Soft Keyboard.

Traditional Chinese - UNICODE.

When you have the time, attach an example text file to a reply post, and if the changes required to my files are small, I will implement them over the weekend.

I still haven't got TangoBlaster going properly... I am somewhat of a Linux noob, I have been using Ubuntu for only two weeks.

Is there an installation walkthrough or FAQ that you know of?

 - I have Java 6 installed.

Also I downloaded the fonts, but for some reason I can't seem to get them into the font:/// directory....

Again I am noob.

Thanks!

---

### Post by ryukent on 2007-03-08
Linux (especially Ubuntu) can be a bit of a pain for fonts and there is more than one place where they need to be registered to work properly. If you've got Java 1.6 installed and can run TangoBlaster, I suggest selecting the font file manually in the font config menu as it is the quickest way to get it working..... of course you probably want to use the fonts in other apps too...

---

### Post by blore123 on 2007-03-09
RyuKent's website is easily the best set of instructions available to work this program, there are other ways of doing the same things, but they invariably depend on what settings you have and what settings you want in the end besides TangoBlaster working ok.

I suggest you stick to the Website, and post to here if you've any trouble. I did and it worked fine for me. A lot of the problems you'll see in Terminal are mundane in reality - it is just that Terminal is great at making them look critical! (Believe me, Windows would do worse if you saw what it is doing in the background when that progress bar is making its steady way from left to right!)

Personally, I found that the fonts are the most questionable point here. If you're writing Tradtional Chinese and use Gyoyu in place of Kana for instance, I've discussed how I used a font in place of RyKents MSGothic because you'll not be able to do Traditional Chinese on that font (not all the time anyway, and not at all for the Gyoyu).

Like I said, if you get a Terminal error or cannot do something, type it here or just goto Applications and use the screenshot utility to show me a picture, or better still: copy and paste it here (but with smileys disabled please!) I should be able to at least tell you what's up within about 24 hours of you posting. Less on a weekend!

Hope it goes well. I'll review the Traditional Chinese when I can, but I need to know if you are writing it as Traditional Chinese (HK) or Traditional Chinese (TW) - I am reliably informed this difference is important...

Thanks for your help, and hope to speak soon (not that I want you to have to send me error messages, just to help with the program!)

---

### Post by FaceLeg on 2007-03-09
Hi,

I got it going - I have to navigate to the folder and double click on the 'tangoblaster.bat' file, but it works...font and all.

Any tips on getting it into the Applications menu?

TIA

---

### Post by FaceLeg on 2007-03-09
I tried to make a .CSV file with the following format:
```

You,n&#464;,&#65279;&#20320;  
Good;well;fine;O.K.,h&#462;o,&#22909;
Ma,ma,&#21527; 
```

And attempted to import it into TB.  

It told me 'No Data'.

Sorry for the noob question...

WAIT!  I found help on your website.

Mike.

Ok I made a .CSV file that successfully imports into TangoBlaster (a great piece of software).

Neither the character, pinyin nor the English display correctly though.

The font I used in OO.org was Kochi, saved in UTF-8.  If I open the .CSV file in text editor everything looks great:

"you","&#25105;","n&#464;","good; well; fine; O.K.","&#22909;","h&#462;o","question particle","&#21527;","ma","I; me","&#25105;","w&#466;"

But none of this will display in-program.

What am I doing wrong?

---

### Post by blore123 on 2007-03-09
Hi, not used Kochi - if you go back over the forum you'll see what I used. I have opted for the Gyoyu rather than the Pinyin approach (I guess you are using Trad. Chinese (HK) as opposed to (TW) variant).

The reason you were not getting data recognised (I think) was that you were either trying to force .csv format to a file that wasn't, or the data was not as mine is. If you use OpenOffice Calc, you can make a three column by many rows spread sheet and just enter Englsih, Pinyin, Chinese that way.

---

### Post by trippinnik on 2007-03-11
I've been using the Tango a bit more.  It's excellent, I  finally have an easy way to study kanji on the train.  I did want to look at the source code though, but I can't open them from the package.  Where can I get the source.  I'd like to help out and I have a feature I'd like to try to add.

---

### Post by blore123 on 2007-03-12
Actually RyuKent, I'd like a look at it too. I don't even do Java, but I have found examining other's code a good way to learn most programming methods. I may even be able to help with any more of my new ideas once I get a grasp on it.

I was meaning to ask you before, but now it appears I'm not the only one who wants a peek...

:)

---

### Post by ryukent on 2007-03-13
Oh source ahh yes, will be available soon. I've been doing some major work these past few days and there's not a currently finished version to look at yet. Will try and make it available ASAP. If anyone is interested, please contact me using the form that will shortly be on the website. In the mean time, I will entertain all questions.

Addressing the CSV issues discussed here recently.

CSV stands for comma separated variables. It is a text file and should be no different from a txt file, but for the syntax that the files must be written in. Tango Blaster accepts UTF-8 encoded CSVs (not the ones defaultly produced in Excel. Also it reads the in the following way.

"English","Reading","Kanji"

You must put the file in that format for it to be read properly. Note that all strings are enclosed in inverted commas and that they are separated by commas. If you use single inverted commas or tabs to separate the variables, they will not be read.

Because UTF-8 (Unicode) is used for the encoding, it will read any language on Earth that can be Unicode encoded. Chinese will work 100% in all formats. However, the important factor then become displaying the text. Now, Tango Blaster does not read fonts from the same place that GTK or QT (Gnome, KDE) programs do. The standard repository Java installations do not set up asian fonts properly. This is partly because SUN hasn't released a final version yet and partly because the people who pack the Java repository packs don't care about non western fonts.

The simple solution is to use a TTF font directly in Tango Blaster. This means you select the font from a file, not from  the system list. If the file supports the Unicode map that you are trying to display then it will show the characters correctly. So, find a TTF that supports your language (msgothic.ttf for Japanese) and in the config menu, set the font to that file. Save the settings (making sure you've tested the font) and then it should display in the test window.

Any problems, please ask here. Please state what character you are trying to display and what font you are using. Please also make sure you have tried linking directly to the font and not just selecting the one from your system list as your system may not be configured correctly.

I am currently in the process of starting a C++ native version of the app using the QT toolkit. This will have better font support, but will not work on anything other than a x86 dist of Linux and will not have database support. I still believe that Java is the way forward. I do not consider the native version a priority. An AJAX web version is also in the pipeline.

For feature requests, please post here for the time being. I am very interested in adding things that people want.

---

### Post by blore123 on 2007-04-01
Incase you guys are still here, reading this...

I presume you are busy, Ryukent, and that's why no source has been made available for us to peek at, either that or like me you're a hacker and you still getting it ready for public viewing as my programs are written from pure thought and contain zero commentary as such, not making them great for viewing until I've combed through it dropping commentary as I go.

Either way, I have those numbers I promised you, it is a data set of about 114 items (!) Moreover I would like this program to goto version one and release to a Linux Distro (hey, perhaps Ubuntu is a good plan!) fairly soon. I reckon you've worked on it enough and data sets will com in from third parties much more if people like it that much, benefitting all learners of Japanese and Chinese (and Korean, I think).

Let me know if this is possible...

Thanks :)

---

### Post by ryukent on 2007-04-02
Yeah, still here. Been off for two weeks showing friends around. Source.... I'll send you a copy when I get home tonight.... it's half way through a new version though so it probably wont compile. And yes as you suggested, there are zero comments and it evolved and was hacked about with so will probably make no sense to most people. Not to mention the blatent inconsistent coding styles, but anyway..... about putting it into a pack... yeah. SUN Java 6 is now in an official Ubuntu pack now (took a while didnt it) so shouldnt be a problem, but I havent packaged anything yet, so might take me a while. Upgraded to Feisty.... oh dear... love some of the new features.... hate the fact that SCIM-XIM doesn't work properly in non GTK/QT apps. TB doesn't need it anyway though, so no probs. Thanks for the numbers. Can I put your sets on my webpage?

---

### Post by blore123 on 2007-04-02
Sounds like you program just like I do!

You are more than welcome to put these data sets on your website, and indeed anyone who downloads them is free to further distribute them freely, although I'd appreciate a mention in any credits created in programs that then use them ;)

I cannot guarantee the quality of them is 100% perfect, but I do my best!

Thanks :)

---

### Post by blore123 on 2007-04-03
Ok guys, what's next for data? Please post what you would like me to do:

1. Grade 2 Kanji (100 Government approved Kanji with English and Kana)
2. Conversational Phrases (A sample set of day-to-day phrases that are useful)
3. The Radicals (214 Kanji Radicals Essential to the Language)
4. Chinese (Simplified, starting from dead basic stuff)
5. Chinese (Traditional, starting from dead basic stuff)
6. Anything else (please state what, or I obviously won't know!)

Whatever gets the highest vote will take priority, if you choose 6, please keep it sensible (no 'please copy out Nelson' requests) and no duplicate votes will count. Voting stops on 15th April when I will pick this up, count the votes, publish the result and get to work.

Thanks for your time :)

---

### Post by blore123 on 2007-04-09
Nice to see there's lots of reply to this.

Just thought I'd share something with you guys in my 100th post.

I have made some custon-modifications to my keyboard. A picture will be attached to this when I get around to it, as you have to see it to believe it.

Those of you from Taiwan will know about this. My gf was going to send me some stickers which cost TWD280 for ten sheets. Thing is, I decided they'd peel off with sustained use and also make singling out keys for terminal usage a nuisance, so I painted the keyboard myself!

The reult is an ergo-keyboard in UK-EN format with all these guoyu on it, and it is now varnished in spray-on varnish to make it wear-resistant. This has had the added bonus of making it look very clean as well (I obviously had to wipe it over and then paint it first).

I should point out to any would-be Traditional-Chinese dataset authors that this keyboard is about an order of magnitude faster than using the the IME or SCIM that comes with the relevant OS as standard. Do it carefully and you'll be rewarded.

Like I said, you'll get a picture soon. :)

---

### Post by Antioch on 2007-04-10
Great program. Haven't used it yet, but it looks like it should perform well. I tried fiddling around with the idea of making a flash-card style program to learn vocab with, but I ended up deciding it wasn't worth the time writing/debugging the code when I could be studying instead. Heh.

Anyways, now that this program is out there it'll be easy to switch to "digital learning."

I appreciate the work and offer my help if you need it.

---

### Post by blore123 on 2007-04-11
In my opinion, these are the two best ways to help us:

1. By using the program. This way, you can suggest ways for the TangoBlaster program to be altered or improved as you may have sen earlier in this thread. It isn't much use writing a program if everyone using it hates it so much they get fed up with it, so that helps a lot.

2. Writing data sets. I'm doing this a lot at the moment, and it isn't great fun, to be honest. However, in its defence, I will say that people benefit from the data sets if they are put together well in a very real way. Databases are largely ineffective here, as the amount of data involved does not work well with TangoBlaster and the way it works. If you look at the sets I have have put together, you will see what I mean, they focus on a single topic or level of learning and are not much bigger than 100 or so items. I hate to say this, but I've also found that writing data sets works best in M$ Windows and in Notepad, saved as UTF-8 .txt files rather than all this SCIM-created OpenOffice .csv files stuff that I have seen. I've never had any problem bigger than having to change TangoBlaster's file filter to 'All Files' on importing sets with Notepad .txts, but I have lost sets in OpenOffice and got stress from trying to get to grips with SCIM, which has about a dozen input methods for Chinese-(Tr) and is, in my opinion, vastly inferior to the IME you get in windows. (And a painted keyboard :))

---

### Post by ryukent on 2007-04-13
Right... here's a question.... I now have in the region of 5-6000 words that have been manually entered.... only problem is, they are in no real order. Suggestions?

---

### Post by blore123 on 2007-04-13
I would need to know more about the data RyuKent, but I'd say the best bet is to manually sort it too.

It's a bit like a messy room. It isn't much use to a person walking in, but if they sort through it, they find useful stuff, put it into groups and know how to get to it!

How much free time do you have?!

---

### Post by Antioch on 2007-04-13
Yes, but it should take less time than you think as most related words share similar kanji parts. :KS

---

### Post by blore123 on 2007-04-14
True! 

You can maybe do a sort by first kanji, that ought to cut the task down to size a bit, thanks for that Antioch!

---

### Post by ryukent on 2007-04-20
Yeah, I did think about those ideas, but if I want to wort by primary Kanji, there's no problem. Thing is I will then get a few thousand lists with few entries on each. Plus, a lot of these words are multiple Kanji compounds and the meaning is not simply displayed in the first Kanji. I think for the time being, I'm gonna release JLPT 4, 3, 2 Vocab and then batches of other stuff in the order I learned them as there was a loose connection (e.g. revolved around an article).

Manually sorting is a little difficult as there are so many ways things can be related. A meaningful relation ship is the most important I think. If anyone out there knows where statistical data on word frequency usage (NOT KANJI usage, already have this) can be found, that'd be great.

All this is slightly on hold as I am currently building Grammar Blaster.... Eventual idea is to merge these two with some Kanji stuff I've been working on and make a general Japanese learning tool.

Blore, if you have time, I might send you an early test release of my grammar app if thats ok.

---

### Post by Antioch on 2007-04-20
Well, in a month or so I will be writing my own databases that I can send off to you. But they aren't really in any order, per se. They're in the order my workbook has them - it's "Kanji in context" by the Japan Times. It covers all the general useage kanji and I assume they're presented in some sort of related order.

A BunpouBlaster is an interesting idea, but I'm wondering how it would work? I have a fat Japan Times grammar dictionary sitting on my shelf, but I can't begin to think of a way to compress it into any sort of flash-card "test."

Anyways, I look forward to seeing how you chose to make it work! =)

Good luck!

PS - I think it should be named BunpouBlaster if the other one is named TangoBlaster ;) Heh.

---

### Post by Antioch on 2007-04-20
Also, I've yet to try TangoBlaster (but am planning on it - just haven't gotten around to setting Japanese up on my new Feisty yet), so you can disregard the following if it is incorrect:

If what I'm seeing from screenshots is correct, there is a mode where it quizzes you. It displays a kanji, it's reading, and it's meaning and you pick whether it is correct or not. If this is so, Im going to further assume that the program randomly picks a hiragana entry from a keyed dictionary array of parsed inputs from the vocab. file and that it picks a random hiranaga for every kanji when in quiz mode.

IF my assumption is true then I would like to suggest the following:

Instead of randomly picking a hiragana for every kanji, the program should do a smart random selection. What I mean by that is based on my previous suggestion: if there are any words that share similar kanji with the current vocab word (whether it be the first kanji in the compound, the second, or third) then that hiragana should be chosen for the test. Then, all of the similar readings be put in an array from which they are randomly chosen.

Reason being is that it's too simple to guess that a given reading is incorrect if it's just too different, or you happen to know the "dai" reading in "daigaku" but the random hiragana reading is "tabemono" you would instantly know it is wrong. But, if the "smart" random function picked "daibutsu" you might stop for a second and think, "well I know the first kanji is 'dai' so I'm going to guess this is right."

Anyways, I hope you understood my suggestion =)

---

### Post by blore123 on 2007-04-21
Ryukent, if it is that bad, I will MANUALLY give you lists of sorted by primary Kanji data and you can use those, just say which Kanji you want doing and I'll copy Nelson, we will never hit the 10% copyright limit like that!

---

### Post by trippinnik on 2007-06-04
Does anyone have a list of the Kanji needed for the Japanese proficiency test?  I like that TangoBlaster can read in txt files with that stuff and I want to focus on the most necessary ones.

---

### Post by trippinnik on 2007-06-04
Oh, nevermind it's already in there isn't it?

---

### Post by thestig_992 on 2008-01-30
> **anoir said:**
> Hi,

I found a program, langdrill, by quick search with synaptics. I'm not sure you like it or not, but it looks quite nice at least.

[lagdrill website]("http://storm.prohosting.com/borco/programming/langdrill.html")

A screenshot in flickr
[[IMG]http://farm1.static.flickr.com/134/357014559_807f94f927_o.png[/IMG]]("http://www.flickr.com/photos/67189739@N00/357014559/")

I went to the site that you gave, but you had to be a paying member to  download. Is it possible to get this game for free or must you pay.

---

### Post by ricoris on 2008-03-30
Hi!
I'm practically an absolute beginner in Ubuntu. I study Japanese and I intend to start Chinese next year. I need to know how can I write Kanji and Kana in my computer. I have been trying to fix it following the HOWTO in [http://www.linux.ryukent.co.uk/show.php?id=25](http://www.linux.ryukent.co.uk/show.php?id=25) but I have trouble understanding what "So copy your downloaded ttf files and paste them into a folder under the fonts tree. I recommend:

/usr/share/fonts/truetype/msttcorefont" exactly means. I also don't understand how it works once installed. 
By the way, I will be happy to offer what I can to any people developing programs for learning Japanese if you just explain to me what I should do. I have a Furigana dictionary and a quite good spanish kanji dictionary which includes different equivalent to the kanji in spanish (which I could translate into English easily) and examples of how the kanji is used in words that include the word written in Japanese, its pronunciation in romanji and different spanish equivalents (which I could translate too) for the word. If anyone is interested in this or other kind of linguistic feedback, just e-mail me at [email]gabi_at88@hotmail.com[/email] and I'll see what I can give you.

---

### Post by FrankVdb on 2008-04-01
Use SCIM on GNOME and SKIM on KDE to input Chinese and Japanese characters. 

I use SCIM and I'm quite satisfied with it. I don't study Japanese

By the way, a good freeware dictionary is Wakan, offering both Japanese and Chinese. Unfortunately, it's Windows stuff. I'm using it on a virtualized XP machine but in the past I got it to work under Wine without much hassle.

---

### Post by TokyoYank on 2008-05-30
> **ryukent said:**
> I think for the time being, I'm gonna release JLPT 4, 3, 2 Vocab and then batches of other stuff in the order I learned them as there was a loose connection (e.g. revolved around an article).

First of all, a huge THANKS for TangoBlaster!  Very handy, useful program.

Second, in Hardy Heron, I could get the program to a useable state without having installed Java packages directly from Sun.  
System > Administration > Synaptic > Search > java  
The relevant packages I have are openjdk-6-jre (and related programs) and perhaps also ubuntu-restricted-extras  (It took me a while to realize that "Java 6" and Java 1.6 were the same, so having a Synaptic way to do this might be useful to others too)

Note, however, this method is not 100% perfect, because there's some jarbled text in the CSV import dialog (the field that shows the file location) and the character next to the kanji (perhaps &#23383; ?).  But during the test, all kanji display correctly.  In addition, I've seen clipped text, no tool-tip or wrapping, when the English definition is too long.  

If anyone reading knows different packages in Synaptic (for example sun-java6-jre?) to avoid these issues, please post up.

Third question, are there JLPT csv files available?  The J501 files I got in the zip file seem more like personal study files, and they don't include the terms I found in lists online.  The files should be a piece of cake to reformat, which I can do if you like.
[http://www.thbz.org/kanjimots/jlpt.php3](http://www.thbz.org/kanjimots/jlpt.php3)

---

### Post by ryukent on 2008-06-10
Thanks for the interest everyone. I know this project hasn't been updated for a long time. I have addressed a number of issues raised here and will try to upload a new release as soon as I get time.

For those using the openJDK version of Java (based on IcedTea) as opposed to the sun version, there is a problem displaying Japanese characters where the font hasn't been explicitly set. TangoBlaster was designed for Sun Java though and will experience best results (and buttons that are the correct size) using the official Sun version.

I've posted a solution in the following thread:

[http://ubuntuforums.org/showthread.php?t=824375](http://ubuntuforums.org/showthread.php?t=824375)

---

