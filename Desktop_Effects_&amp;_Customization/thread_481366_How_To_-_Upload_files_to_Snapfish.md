---
title: "How To - Upload files to Snapfish"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by DugieHowsa on 2007-06-22
I am recently switching over to Ubuntu as a full-time Desktop OS.  One of the hardest parts of this though is having it pass the ever critical wife test.  So far, wife testing is going well, as she is comfortable using firefox, openoffice and pidgin.  But we hit a bump in the road recently when she needed to upload a bunch of pictures to Snapfish.  She used to use a Snapfish utility in Windows to do bulk uploads.  This option was not available for Linux users, and she certainly was not going to use the standard browser interface to upload a single picture at a time.

The answer?  Nautilus Scripts!

Now I can't claim the idea for my own.  The following two posts helped me tremendously in getting this working.

[http://heliolith.com/archives/2006/05/26/uploading-photos-to-snapfish-on-linux/](http://heliolith.com/archives/2006/05/26/uploading-photos-to-snapfish-on-linux/)
[http://ceitl.zanestate.edu/blog/archives/2007/05/script-email-from-nautilus/](http://ceitl.zanestate.edu/blog/archives/2007/05/script-email-from-nautilus/)

Both had bits and pieces of functionality I wanted.  All I had to do was blend them together.

1)  Create a Google Mail account if you don't already have one.

2)  Add this Google Mail account to your Snapfish preferences to accept pictures from e-mail.

3)  Install mutt and zenity if they are not already installed:
Code:
	sudo apt-get install mutt zenity

4)  Download the putmail.py python script;
	[http://sourceforge.net/project/showfiles.php?group_id=122444](http://sourceforge.net/project/showfiles.php?group_id=122444)

5)  Extract and install the script:
Code:
	tar -xvf putmail.py-1.4.tar.bz2
	sudo ./putmail.py-1.4/install.sh

6)  Create a mutt configuration file for your profile:
Code:
	gedit ~/.muttrc

7)  Enter the following data into the file and save it:
	set sendmail="/usr/local/bin/putmail.py"

8)  Create a putmail directory in your home directory:
Code:
	mkdir ~/.putmail

9)  Create a putmail configuration file:
Code:
	gedit ~/.putmail/putmailrc

10)  Put your Google Mail information in it:
	[config]
	server = smtp.gmail.com
	email = [email]youruserid@gmail.com[/email]
	username = [email]youruserid@gmail.com[/email]
	password = yourpassword
	port = 587
tls = true

11)  Download the following script:
	[http://ceitl.zanestate.edu/blog/wp-content/uploads/2007/05/2gmail.txt](http://ceitl.zanestate.edu/blog/wp-content/uploads/2007/05/2gmail.txt)

12)  Copy it to the Nautilus Scripts directory and rename it.
Code:
	cp ./2gmail.txt ~/.gnome2/nautilus-scripts/SendToSnapfish

13)  Open the script file:
Code:
	gedit ~/.gnome2/nautilus-scripts/SendToSnapfish

14)  Make the following change:
	a) Change to="you@work.com" to to="save@snapfish.com"

15)  That's it.  Now all you have to do is right click on one or multiple files, choose scripts-> SendToSnapfish, and they will be sent to your Snapfish account!

---

### Post by DSn0wMan on 2007-06-22
I think I am just going to let my wife upload the files one at a time for now. Thanks for the post though. I never would have thought of this on my own.

---

### Post by www.rzr.online.fr on 2008-01-13
Maybe we can report a wish to fspot project ?
--
[http://rzr.online.fr/q/picture](http://rzr.online.fr/q/picture)

---

### Post by billbog on 2008-01-15
I had a problem uploading photos and found Google Picasa worked well .

---

### Post by AdrianStrays on 2008-05-11
I followed this, but I don't see the scripts ->SendToSnap fish option anywhere....

---

### Post by Dr.Ninethousand on 2008-05-28
> **AdrianStrays said:**
> I followed this, but I don't see the scripts ->SendToSnap fish option anywhere....

same here..

---

### Post by Life On Mars on 2008-07-06
> **Dr.Ninethousand said:**
> same here..

Did you change the permissions on the new file you created "sendtoSnapFish" so that it is executable as a program?

Go to /.gnome2/nautilus-scripts/ right click then select properties > permissions and check the box to allow executing file as a program.

---

