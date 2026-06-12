---
title: "Can somebody recommend a good diary/journal program?"
date: 2009-03-17
forum: General Help
---

### Post by tegnoto89 on 2009-03-17
I'm thinking about starting to keep a diary, does anyone have recommendations on a program that might work?  If it's not password protected, can somebody explain how I can lock it manually?

---

### Post by Herman on 2009-03-17
Here's a link to a diary program, (I haven't tried it but probably it's good), Almanah Diary - [http://tecnocode.co.uk/projects/almanah/](http://tecnocode.co.uk/projects/almanah/)

Also just a plain ordinary text editor is all I need. 
Gedit text editor has an 'add time and date' function as do other text editors.

If you keep logging things in the same format, you can use the grep command to good effect on a text file.
For example, if you choose keywords and always begin lines or paragraphs to do with that subject with the same keyword, you can easily grep the keyword.

For example, if you want to be able to easily add up your expenses for the year, and if you put the word 'expenses' at the beginning of each line that records what purchased and how much you spent, just grep 'expenses', for a list of all your expenses.
If you headed your line 'expenses - petrol', then you can grep petrol, for a list of all of your petrol purchases for the year. 

As for encryption, seahorse comes with Ubuntu, [Set up Seahorse]("http://users.bigpond.net.au/hermanzone/p5.htm#Install_Seahorse")

You can also make a file hidden by typing a dot before the rest of the file name, most people know that trick, but it's still worth doing. A casual snoop may not have time to think of it..

---

### Post by halovivek on 2009-03-17
thanks for the reply. I was using dairy in windows. now i will start using it Ubuntu also.

---

### Post by ellgor on 2009-03-17
Hi, 

Take a look at "Kontact",its got everything you might need?

Regards, Ellgor

---

### Post by Herman on 2009-03-17
It's fun and useful to learn a few linux commands.
If you are keeping a diary or log in a plain text file, and you might want to add up your expenses after a period of time, you can do that easily providing you have planned ahead.
Providing you keep to the same format for your interesting lines, you can have any kind of story (prose) entered between the lines for each day's events. 
For the lines that may be of interest at a later date, if you can choose a format and stick to it, (by copying and pasting an example line), you can do something pretty neat with linux commands.
Your lines that will be of interest later on should contain 'keywords', and be entered with commas separating each value. 

A 'csv' file is a plain text file with 'comma separated values' (.csv). If you name a file with the .csv filename extension, Ubuntu will open it with Open Office,org spreadsheet.

The grep command can find all of the lines that contain a keyword.
I have keywords 'expenses', and 'petrol' in my log.
If I grep 'expenses', I'll get a list of all of my expenses.
If I grep 'petrol', I'll be presented with a list of just my petrol expenses.

For example,
```
 grep 'Petrol' 2007_log.txt
```example output, (in terminal)```
Expenses:, Petrol:, $ 60.45, for, 45.53, litres @, 132.77, at V-8 Hughenden, ,ready for tomorrow's journey.
Expenses:, Petrol:, $ 67.82, for, 56.66, litres @, 119.7, at Shell Garbutt Townsville, 09:28 EST.
Expenses:, Petrol:, $ 50.02, for, 42.43, litres @, 117.9, at Mobil Atherton, 03:55 EST.
Expenses:, Petrol:, $ 59.85, for, 47.20, litres @, 128.8, from Malanda Bulk Fuel, 17:38 EST, In Jamie's car since I borrowed it so many times.
Expenses:, Petrol:, $ 42.93, for, 36.11, litres @, 118.9, from Orange Glacier Portsmith Atherton, 12:04 EST.
Expenses:, Petrol:, $ 56.02, for, 50.06, litres @, 111.9, at Mobil Atherton, 20:27 EST.
Expenses:, Petrol:, $ 50.00, for, 44.68, litres @, 111.9, at Mobil Atherton, 10:33:15 EST.
Expenses:, Petrol:, $ 57.25, for, 50.73, litres @, 112.9, at Cairns BP, 06:19 EST

```The grep command has pulled these lines out of a huge amount of other text which mainly consists of prose.

Now, for the next step, if I had used a command as follows, instead of just seeing the output in my terminal, I'll add it to a file named petrolpurchases.csv,
 ```
grep 'Petrol' 2007_log.txt >> petrolpurchases.csv
```Now when I click on the file named petrolpurchases.csv, it opens in Open Office,org spreadsheet and I can make use of the data.

In order to do that I needed to plan ahead and format my data the same way, with commas separating the values that I want to appear in each colimn of my spreadsheet later on someday.
It's not hard to do, and can be worth it later on. ;)

Linux commands are fun and useful as well.

---

### Post by Herman on 2009-03-20
I'm trying out the Almanah Diary and now that I have seen a few things I can do with it I really like it. I'm a convert.


[LIST]
[*]Almanah has a nice 'search'  function.
[*]It's easy to go right to a date just by clicking it on the calendar at the top of the right-hand pane.
[*]It's easy to create a link in the right-hand pane to any file, so we can easily keep our extra details in separate text file, .cvs or spreadsheet simply by clicking the link for it, no need to jumble everything together in the first place.
[*]The file is automatically encrypted for privacy, so we don't need to waste time encrypting/decrypting manually.
[/LIST]
I think I'll be installing it in every new Ubuntu installation I do from now on.  It should be a standard program.
It could do with a proper icon of it's own. 

Almanah is cool! :D

---

### Post by tegnoto89 on 2009-03-21
I'm having some trouble installing almanah, I get it and extract it, but it's a file full of different things, and I don't know what to do with it.  I tried putting it in usr/bin  but it gave me an error.

---

### Post by Herman on 2009-03-21
If you're running Intrepid Ibex or if you're a Jaunty Jackalope tester, Almanah should be in your repositories.

First make sure you have [enabled all of the repositories]("http://users.bigpond.net.au/hermanzone/p5.htm#Enable_Standard_Repositories") in your /etc/apt/sources.list file.

You should be able to find almanah in your 'Applications'-->'Add/Remove Programs' list, you will probably find it quickest to use the search function.
First check that 'All' categories are highlighted in the left-hand pane. 
Make sure the 'Show:' spinbox is set to 'All Available Applications', or at least 'All Open Source Applications'.
Now the search function has the best chance of being able to find it.
Once you have found it with the search function, you just click on the checkbox to mark it and click the 'Apply Changes' button down in the bottom right-hand corner.

If you're running Hardy Heron or older, it probably isn't in your repositories. (It doesn't seem to be in my Hardy Heron repositories).

Here's a review about almanah which says we only need to install a C compiler first, then we should be able to install the tarball in Hardy Heron, [Almanah Diary Review]("http://www.softpedia.com/reviews/linux/Almanah-Diary--Review-90230.shtml").
> Almanah Diary is available as a source package, so you will have to "work your fingers to the bone" by installing its dependencies and going through the three magic steps of installing something from source: ./configure, make and make install. If you're using Ubuntu, you will have to install even a C compiler, as Ubuntu was probably designed for persons who are scared of the shell and just want to install pre-compiled .deb packages from this distro's repositories or from third-parties. I like Ubuntu, but it still lacks some basic development packages. :( Some of that is a matter of opinion. It's not that we're 'scared of the shell'. It's easier to install from .deb packages but the other reason why we prefer to install from .deb packages and only get out software from Ubuntu's repositories is for security reasons. Only developers with the proper gpg keys are allowed to upload to the official repositories, and that protects us from rootkits and other nasty programs. (I'm not implying that almanah would have a rootkit, but the potential is there when we install software from 'unknown' sources, so installing from tarballs is not a good habit to get into). [SecureApt - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SecureApt").

I have tried the old fashioned tarball method anyway and so far I'm in 'dependency hell'. It's a lot easier to just upgrade to Intrepid Ibex or install Intrepid Ibex if we want to be able to easily and safely install almanah.

---

### Post by tegnoto89 on 2009-03-21
Ugh, what a drag.  I downgraded from Intrepid because it apparently does not work with WPA2 wireless, so I wasn't able to use it at college.  Thanks for the responses!

---

### Post by Herman on 2009-03-21
> Ugh, what a drag. I downgraded from Intrepid because it apparently does not work with WPA2 wireless, so I wasn't able to use it at college.Yeah, I know how you feel, it's a drag for me too. I still use Hardy Heron because I like Kompozer, and that doesn't work too well in Intrepid yet.  (Except if I use an alpha version of Kompozer 0.8 ).
I'd prefer to be able to use Intrepid as my main operating system. 
I'm multiple booting, but that doesn't mean I enjoy rebooting to use a program that doesn't work in whatever version of Ubuntu I happen to have booted at the time. It's rather inconvenient but it looks as if all we can do is be patient and compromize for now by using gedit, or Kompozer for now and try to be happy. Or use a newer version of Ubuntu and do without something else.

---

### Post by TedBuckland on 2009-05-03
You could also try this diary/journal program:

[http://rednotebook.sourceforge.net/](http://rednotebook.sourceforge.net/)

---

### Post by jonboy99 on 2009-05-10
Been looking for a diary program too, password protection and encryption essential.  Almanah doesn't have it unfortunately so no good for me.

Found this program - mydiary:

[http://linux.softpedia.com/progDownload/myDiary-Download-35861.html](http://linux.softpedia.com/progDownload/myDiary-Download-35861.html)


Seems to work ok, though I needed to install python-gnome2-extras from the repos (in jaunty) to get it to install. 

Maybe someone who knows more can say how strong the encryption is?

---

