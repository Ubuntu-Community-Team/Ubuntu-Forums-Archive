---
title: "What's the easiest way to make a directory system?"
date: 2010-05-24
forum: Desktop Environments
---

### Post by sidewalkcynic on 2010-05-24
I have a text file, a list of about two hundred words, indented to simulate a tree directory.

I would prefer not to have to create and name the folders - I want to plug the list in, or type the words in.

Anything to make it easier than creating folders and then typing the designations.

---

### Post by tgeer43 on 2010-05-24
Hi sidewalkcynic,

More than likely there is already something out there to do exactly what you want. I took a quick look and didn't turn anything up but it was a *very* cursory search - you'll do better, I'm sure.

Barring that, if you have any coding experience at all, just about any scripting or programming language should provide the necessary functions.

The quick & dirty way would be to write a simple bash script to read in each line of your input file, parse it, and use the result to create the corresponding directory on disk.

If you get your text file to me I will try to find the time to give it a go. If you don't want to attach it to a reply here, feel free to pm or email me.

tgeer

---

### Post by sidewalkcynic on 2010-05-25
Yeah, I have been searching myself. And, I have been assuming that it has to be a programming language, and I am bankrupt on programming - got to take the time and figure it out someday.

My deal is, I am devising the ultimate personal documents directory system with links, but when I make changes it can be a hassle, and is easier to start from scratch; but that gets tiresome in GUI - creating folders. So, I was hoping to find the script text document and do the cut and paste method. I'm sure it's out there . . .

---

### Post by tgeer43 on 2010-05-25
As I stated in my first reply, if you will send me the text file (so I can see the exact formatting/encoding), I will do my best to whip up a shell script to do the job for you. In fact, I've already started but I am nearing a standstill until I see your file. Oh, and there won't be any need for cut and paste, either. You will just run the script with the name of your "tree" text file as a parameter, like this: ```
*./myscript.sh mytextfile.txt*
```It will read each line of the file and create the corresponding directory.

You can attach the file to a private message here on the boards or as a regular email attachment. Just click on my user name in the top-left of this message.

I'd been looking for a short but useful programming exercise (just to keep the old noodle sharp, ya know) and this might be just the ticket.

tgeer

---

### Post by sidewalkcynic on 2010-05-27
I installed gnome-commander, and I am going to try it out - maybe it will be of benefit to what I am approaching.

---

### Post by Spacestationmax on 2010-08-11
What happend to this project?

---

### Post by tgeer43 on 2010-08-18
Well, for starters real life intervened (it has a nasty habit of doing that). ;)

Also, I never received the directory structure file that I requested from the OP. I still have the script that I started laying around here somewhere. If given the specific data to be worked upon, I'm still willing to try and find time to whip something up but I definitely don't have enough spare time to write something that is going to work on a wide variety of input files. It would have to be a case-specific, quick & dirty script.

Regards,

tgeer

---

