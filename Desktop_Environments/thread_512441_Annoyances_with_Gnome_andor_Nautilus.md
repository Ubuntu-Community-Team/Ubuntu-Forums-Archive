---
title: "Annoyances with Gnome and/or Nautilus"
date: 2007-07-29
forum: Desktop Environments
---

### Post by Batuhan on 2007-07-29
Hello all! 

I've made the switch quite some months ago and loving every moment of it.
However I have some annoyances with the way I interact with my system and I'm asking for your help.

1. When I "unmaximize" a window, it ALWAYS stays in the same  size but makes the borders resizable. I want to be able to have a custom size for a window when it is unmaximized, because if I unmaximize to see another window on my workspace, I have to go and find the border manually and resize/move the window everytime I do this. This is very annoying for me. So when I click unmaximise I want the window to shrink in size without me resizing it manually everytime. Any suggestions?

2. File search is extremely painful in nautilus. In file manager, I press Ctrl+f and write the file name. It starts to search... It takes forever and it does not show any results before it finishes searching the WHOLE drive. So if I want to search a file, I have to wait for the whole drive to be searched file by file and when it finishes I have the results. The command line "locate" tool is very handy, I make "sudo update db" if I'm searching for stg new and then "locate filename", works fast and like a charm. Bu I could not find a way to make it work with external drives or other partitions and such. It just works in my Linux filesystem. So how can I have a nice file search system? I'm ok with indexing files beforehand, a tool like locate maybe(maybe locate does what I want but I could not figure that out). Any suggestions on this one?

3. When nautilus finishes searching(see no 2), it lists the found files, but there is no way for me to see where that file actually resides on. It just shows me the file but does not really show where it is! This is ridiculous. I can right click on the file and see properties to see the path to the file, but oh, it is truncated because the path is long! You cannot access the full path from there too! What will I do then?

Advices on these things will be appreciated!
Thanks for your help!

---

### Post by ugm6hr on 2007-07-29
I use Xubuntu7.04 (XFCE) rather than GNOME - thought I'd offer some ideas:

1. XFCE behaves as you would like.  Sorry - can't help with GNOME issue.

2/3. I use Catfish as a search tool - it should work with Nautilus too.  Catfish is a GUI for Terminal commands *find* (quick filename search), *locate* (which you like) and *slocate*.
Available from: [http://www.getdeb.net/search.php?keywords=catfish](http://www.getdeb.net/search.php?keywords=catfish) (easy .deb installation) or the latest version which needs compiling from the homepage linked from there.

I haven't used Nautilius - but I am sure you should be able to integrate it.

I use the command: *usr/bin/catfish --fileman=thunar --path=%f --hidden --method=find* (for Thunar integration and default *find* function).

---

### Post by Batuhan on 2007-07-30
Thanks for the search tips! I'll give it a try.

Anyone will help on this window size issue?

---

### Post by Batuhan on 2007-08-26
Ok, I liked catfish but I can't invoke it "on the place", I mean I go to a folder and want to search within that folder and it's subfolders.

With catfish, I need to run it as root and then browse for the folder and so on...(I haven't been able to integrate it into nautilus)

But it is still useful, I'll be sticking to it for now.

What about the window issue? No one has a problem with that?

WHY would I restore a window if it would stay at the same size?

---

### Post by nandemonai on 2007-09-02
I'm experiencing the exact same thing in Feisty with desktop effects enabled (Restricted NV driver) in Gnome. Everything else seems fine but unmaximizing does not work correctly.

---

### Post by Batuhan on 2007-09-03
I'm not doing well with catfish too, I have to tell after those days.

When it finds the files, you can only open them, but cannot open the containing folder(you have to memorize the path, then go to your file manager, and go to that folder), you cannot copy, cut or drag and drop the found file...

I am amazed by ubuntu for sure, and use it all the time but I can't believe how it makes simple tasks as searching a file and going to that folder(or copying that file from gui) that hard...

---

### Post by ugm6hr on 2007-09-03
> **Batuhan said:**
> I'm not doing well with catfish too, I have to tell after those days.

When it finds the files, you can only open them, but cannot open the containing folder(you have to memorize the path, then go to your file manager, and go to that folder), you cannot copy, cut or drag and drop the found file...

I am amazed by ubuntu for sure, and use it all the time but I can't believe how it makes simple tasks as searching a file and going to that folder(or copying that file from gui) that hard...

Catfish integrates flawlessly with Thunar (default file manager in Xubuntu).  You can install thunar on ubuntu (I believe).

---

### Post by Batuhan on 2007-09-03
Yes, you were absolutely right at the first places. I'm really fed up with Nautilus, I really respect the work behind it but it just wastes my time.

The only guide I've been able to find for switching to Thunar is this:
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

But I have this problem:
If I enter a folder or to a volume from desktop, Nautilus opens. But If I click "places" then select a vlome from there, thunar opens.

What is wrong?

---

### Post by Batuhan on 2007-09-03
I right click to a folder select properties --> Open with
There I can see the option "open folder with thunar" but it is unselectable. It sticks to Open folder option. Maybe I can change it from a .conf file?

Ant I'm trying to integrate catfish to thunar as you suggested:

> /usr/bin/catfish --fileman=thunar --path=%f --hidden --method=find

But catfish complaing: no method- hidden

If I delete the hidden option, then it complains: no method- method

Sorry if I'm asking too much. I'm very close to being happy, i liked thunar very much.

---

### Post by isync on 2007-09-03
See my just posted question related to Nautilus' strange file selection behaviour... (which cost me 150+GB of data in the fraction of a second - when I didn't checked the trash before emptying...)  ;-((

Post: [http://ubuntuforums.org/showthread.php?t=542156](http://ubuntuforums.org/showthread.php?t=542156)

---

### Post by Batuhan on 2007-09-03
Ok I managed to kind of integrate catfish into thunar by the help of this guide/script:
[http://ubuntuforums.org/showthread.php?t=214059](http://ubuntuforums.org/showthread.php?t=214059)

But it still does not do what I want. When I make a search, it just opens a catfish window which has no use at all other than showing the files and their paths. I was thinking that an integration would display the results in a thunar file manager window.

Because I want to:
1: be able to drag and drop the found file to another place(say my desktop) so I ca nwork in a copy of the file
2: be able to go to the parent folder where the file is located in.

So far catfish only has two items in search results found menu, they are open(thanks to that) and jump to(I don't know what it does, it did nothing for me yet).

I would be a wee bit happier if it helped me to copy the file path to clipboard to actually see the file in my file manager by pasting the path but noes... I'm forced to locate the file location manually by hand. This one summed with not being able to copy the file by any means from within catfish is the basis of my frustration with these tools.

Hope I made myself clearer.

Thanks for all the help! At least I'm doing something to make my life easier!

---

### Post by chrisTGc on 2007-10-09
Hi,
Yup i think this Ubuntu OS is great as is Gnome,i even like Nautilus a bit(just a bit).Can understand your frustrations with Nautilus.The 'search for files' is very unreliable,soon after installing Fiesty,after much frustration i went so far as to test 'search for files' where i knew exactly the files name and position and the search would not locate it.Locate or find from terminal is much better.The Nautilus CD burning extension,i find is unreliable also especially with burning my daughters audio CD's,it seems to burn one huge track rather than the 20 or so on the master CD. Thereafter Nautilus cannot understand its own handywork.OK so i realise that serpentine does the job well but why does Nautilus offer the facillity when it cannot do it.

I do find though that if i adjust the window size by dragging the edges inward while unmaximised Nautilus will remember the new smaller size providing i close Nautilus while unmaximised.

lets hope the Gnome developers do 3 things for their fan boys (as regards myself an elderly one at that);
1)sort the problems out with the search for files;
2)give us a way of stopping the Nautilus CD burning extension from popping up;
3)get this unmaximise window reliable.

Otherwise the steady development of Ubuntu and Gnome is just great. 

Best Wishes Chris.

---

### Post by Telecaster72 on 2007-10-10
Why Nautilus shows folder size by items and not the actual size in bytes or MB's is something i do not understand.

I also wish it would show info when holding the cursor over a file or folder, like size (again SIZE not just number of items) or the ID tag when holding it over a ogg or mp3.

Another annoyance is that i cant drag 'n' drop from the side pane.

It would be good to be able to make the icons smaller in "view as icons" like you can scale in listview, and i actually prefer the listview in XP *shrugs* where it builds on to the side and you can see several rows in one window instead of just one long row in Nautilus.

There is ofcourse things i like as well but a little too many things that just doesnt make sense.

---

### Post by mjwood0 on 2007-10-10
I still find Gnome / Nautilus to be problematic for new users.

Personally, terminal searching is much more reliable and faster -- but it comes at the price of not having a gui interface available.

Nothing beats knowing how to use grep though...  very powerful.  I really wish there was a gui interface though!

---

### Post by LuxeSaber on 2007-11-05
> **Telecaster72 said:**
> It would be good to be able to make the icons smaller in "view as icons" like you can scale in listview, and i actually prefer the listview in XP *shrugs* where it builds on to the side and you can see several rows in one window instead of just one long row in Nautilus.

Have you tried Ctrl+(Plus) or Ctrl-(minus) in icon view? I could be confusing it with thunar, but it makes my icons grow larger and smaller respectively. 


> **mjwood0 said:**
> I still find Gnome / Nautilus to be problematic for new users.

Personally, terminal searching is much more reliable and faster -- but it comes at the price of not having a gui interface available.

Nothing beats knowing how to use grep though...  very powerful.  I really wish there was a gui interface though!

I did a search on google for grep GUI and it came up right away, I have not tested it yet, however. It is called Grepui.

[http://sethoscope.net/grepui/]("http://sethoscope.net/grepui/")

EDIT:Found 2 more GUI for grep, both coincidentally called GuiGrep (one is java)

[http://www.urban.ne.jp/home/kanemori/zaurus/guigrep_e.html]("http://www.urban.ne.jp/home/kanemori/zaurus/guigrep_e.html")
and
[http://www.javaregex.com/guigrep.html]("http://www.javaregex.com/guigrep.html")

---

### Post by nutter78 on 2007-11-15
Sounds good - will check it out

---

### Post by benjcrawley on 2007-12-26
As far as I can figure out, the Gnome search assumes that you want to grep all files in a directory to see if what you typed is in there.

i.e. search for *.jpg is taken as find the expression "*.jpg" in the files in the default directory (your home).

you can change the search folder and type of file but it still won't find, it only greps.

I'm going to try some of the alternatives suggested above.

Why do I waste my time on this stuff?

---

### Post by daengbo on 2007-12-27
You will find it much simpler to use the Places menu or Deskbar  to search.
In Places -> Search for Files just select the directory and file name
With the deskbar, enable Search Files and Folders.

If you upgrade to 7.10, the Tracker search tool works quite well from the deskbar, too.

---

