---
title: "Clear some of the recent documents"
date: 2011-10-31
forum: Desktop Environments
---

### Post by Azyx on 2011-10-31
Hi.
I wonder if it's possible in gnome 2.x to clear some of the recent documents (not all)? For instance if you watching i TV-serie you maybe just want to save the last, so you a afterward can see what you already have seen.

Then I wonder if there are something similar in Unity (or gnome 3) as 'recent documents', cos in the future we ali have to leave gnome 2.x.

/Cheers

---

### Post by Paddy Landau on 2011-10-31
Unity has "Files and Folders", which shows recent documents among others.

AFAIK, there is no simple way to clear selected items from the recent files. I believe they are held in a database, and thus would require an application to modify.

In any case, anything you want to keep in the recent files could quickly be moved out. I would suggest you bookmark what you need. You could use a simple text editor to list your items, or create links (shortcuts) in a specific folder you create just for the purpose.

---

### Post by Azyx on 2011-10-31
> **Paddy Landau said:**
> Unity has "Files and Folders", which shows recent documents among others.

AFAIK, there is no simple way to clear selected items from the recent files. I believe they are held in a database, and thus would require an application to modify.

In any case, anything you want to keep in the recent files could quickly be moved out. I would suggest you bookmark what you need. You could use a simple text editor to list your items, or create links (shortcuts) in a specific folder you create just for the purpose.

So sad :( I know in w2k, it was possibly to right-click the recent document to erase it. Tnanx för the advise to bookmark, but I think it to hard to learn ( I don't think about iy untill afterwards );) 

Do you know how I increase the number of recent documents?

/Cheers

---

### Post by Paddy Landau on 2011-10-31
> **Azyx said:**
> Do you know how I increase the number of recent documents?
Sorry, no I don't.

---

### Post by WasMeHere on 2011-10-31
This command displays files in your 'Documents' directory, that were created or modified during the 7 last days. Having seen them, you can select files and do whatever you want to with them.
```
sudo find ~/Documents -name \* -ctime -7 -type f
```
Maybe not beautiful, but it can be very efficient.

---

### Post by Paddy Landau on 2011-11-01
@Olle Wiklund: Nice, thank you.

The find command can be simplified somewhat; don't use sudo unless you specifically need it, and the -name option should use quotes (there are cases where that makes an important difference). However, you don't need -name if you are finding all relevant files, thus:
```
find ~/Documents -ctime -7 -type f
```

---

### Post by WasMeHere on 2011-11-01
> **Paddy Landau said:**
> @Olle Wiklund: Nice, thank you.

The find command can be simplified somewhat; don't use sudo unless you specifically need it, and the -name option should use quotes (there are cases where that makes an important difference). However, you don't need -name if you are finding all relevant files, thus:
```
find ~/Documents -ctime -7 -type f
```
Thanks Paddy,

Doing the same thing in a simpler way is more efficient and more elegant. By the way, I'm not sure about the difference between the testing options *-ctime* and *-mtime*. Can you explain, please?

Thank you :-)
Olle

---

### Post by Paddy Landau on 2011-11-01
> **Olle Wiklund said:**
> ... the difference between the testing options *-ctime* and *-mtime*.
There are three different timestamps: atime, ctime and mtime.

[LIST]
[*]**mtime:** When were the contents of the file last modified? If you create a file, edit a file, or change its contents in any other way, this updates mtime.

A new file created by copying is still a new one, so it gets a new mtime.
[/LIST]

[LIST]
[*]**ctime:** When was the file's status last changed?

If mtime is updated, it also updates ctime. But what if you change the file's permissions, its location or its name? That doesn't change its contents, so mtime doesn't change. But a backup program needs to know that something has changed, and so ctime records this fact.

Incremental backup programs check ctime rather than mtime to check whether or not to back up any changes, because backup programs record not only a file's contents but also its name, location, permissions, owner, and group.
[/LIST]

[LIST]
[*]**atime:** When was the file last accessed (not necessarily read)? This could be the same  time as, or after, the last ctime -- but never before.

For reasons of  efficiency and reduced wear on disks, Ubuntu and some other distributions do not record every access, but only the first access after ctime has changed.

Some programs need to know atime; for example [FONT=Fixedsys]mutt[/FONT], which checks atime to find out whether or not you have read a specific email.
[/LIST]
Generally, you'd want to check mtime if you're only interested in changes to the contents.

Note that folders are also files, so they also have their mtime, ctime and atime updated.

Here is a nice [explanation of ctime and mtime]("http://www.unix.com/tips-tutorials/20526-mtime-ctime-atime.html").

---

### Post by WasMeHere on 2011-11-01
Thank you Paddy,

I could not find it browsing the internet last night. Your description is very clear, so now I understand :-)

Having fun finding out :-)
Olle

---

### Post by mcduck on 2011-11-01
Since you asked how to do this in Unity, here's the answer:

Unity uses Zeitgeist to store this kind of history, so you can use tools like Activity Log Manager and Gnome Activity Journal to control what's stored in the history. (I'm not sure if Gnome Shell is currently using Zeitgeist or some other method, but at least it's going to use Zeitgeist in the future)

Gnome Activity Journal is mainly intended for viewing the history, but it also allows you to remove individual items from the journal.

Activity Log Manager gives you more detailed control about what kind of activities are logged, allows you to exclude items from certain directories or of certain file types or based on application used. It also gives you the option to erase history from a certain time range, or from previous 15min/hour/2hours/6hours/day/week.

edit: Both these tools are available from the [Zeitgeist PPA repository]("https://launchpad.net/~zeitgeist/+archive/ppa").

---

### Post by Azyx on 2011-11-01
I find this to solution to change numbers of 'Recent document' :)

Open, or if there are no file on you home-folder this command create it and open it:

```
gedit ~/.gtkrc-2.0
```Add following line in the opened gedit-document, and save it and close:

```
gtk-recent-files-limit=40
```There the number  (40) may bee the number of Recent document. 0= no document are shown..

/Cheers

---

### Post by Azyx on 2011-11-01
It didn't work :( I find the 'solution' here:

[http://tips4linux.com/turn-off-or-limit-the-recent-documents-feature-in-ubuntu/](http://tips4linux.com/turn-off-or-limit-the-recent-documents-feature-in-ubuntu/)

And read the comment and fint the last that says:

        **         "since this is the #2 google hit        **                       
       [       June 10th, 2011      at       10:05 pm      ]("http://tips4linux.com/turn-off-or-limit-the-recent-documents-feature-in-ubuntu/#comment-3041")                          
      it seems like a good place to point out that this constantly-repeated “method” is NOT true at all.
 all these options do is HIDE the “old” / “excess” entries from the  gnome “recent files” dialog, and even then the gnome docs explicitly say  apps are free to ignore the user’s instructions any time they feel like  it. the spyware^W - sorry, “full history” - is still there in  ~/.recently-used.xbel"


:(

---

### Post by WasMeHere on 2011-11-01
--- (wiped)

But at least, you can use the terminal command way until you find some other method. What about mcduck's suggestion?

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> --- (wiped)

But at least, you can use the terminal command way until you find some other method. What about mcduck's suggestion?

Haven't really started to learn Unity or Gnome3 yet. For instance i want an auto-hide able panel with system indicator, so for now I'm try to learn Gnome-fallback^^ (slow learner). I really like Gnome 2.x and have it both on my netbook and my big screen computer, but on my notebook i auto-hide menues to save space (That work with Gnome-fallback, but are little tricky).

Anyway. In gnome 2.x i find a hidden-file in my home-folder that is a kind of 'spyware'
 that really store all files:

~/.recently-used.xbel

Will see if it's possible to use that. It is a xml-file and hard to read.

/Cheers

---

### Post by WasMeHere on 2011-11-01
The Unity panel (on the left edge) auto-hides, when 'pushed away' by an application window.

---

### Post by WasMeHere on 2011-11-01
Helly again,

The command line way to get
- the *weekly harvest history* or
- the *weekly harvest here*
is an alias, to be entered into ~/.bashrc

```
alias whh='sudo find [COLOR="Red"]*[/COLOR] -ctime -7 -type f'
```

This way you find the files created during the last 7 days in the current directory and its subdirectories. Change directory to another place, e.g. an external disk to do the same there with your new command ```
whh
```

Using [COLOR="Red"]*[/COLOR] (star) instead of [COLOR="Red"]~[/COLOR] (tilde) or [COLOR="Red"]**.**[/COLOR] (dot) avoids reading hidden files. Using sudo avoids error output because of no read access. [Sorry for not listening to your advice about sudo, Paddy ;-)]

Having fun finding out
Olle

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> Helly again,

The command line way to get
- the *weekly harvest history* or
- the *weekly harvest here*
is an alias, to be entered into ~/.bashrc

```
alias whh='sudo find [COLOR=Red]*[/COLOR] -ctime -7 -type f'
```This way you find the files created during the last 7 days in the current directory and its subdirectories. Change directory to another place, e.g. an external disk to do the same there with your new command ```
whh
```Using [COLOR=Red]*[/COLOR] (star) instead of [COLOR=Red]~[/COLOR] (tilde) or [COLOR=Red]**.**[/COLOR] (dot) avoids reading hidden files. Using sudo avoids error output because of no read access. [Sorry for not listening to your advice about sudo, Paddy ;-)]

Having fun finding out
Olle

But isn't that just files in the home-folder? Not files opened from extrernal medias or samba-shares?

---

### Post by WasMeHere on 2011-11-01
Change directory to another place, e.g. an external disk to do the same there with the same command ***whh***

For example
```
cd /media/disk1
whh
```

If the path is long, you can drag-and-drop it from Nautilus to your terminal window :-)

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> The Unity panel (on the left edge) auto-hides, when 'pushed away' by an application window.

It's called launcher and are not a panel, for applet as system-monitors, and so on. You aren't even able to make the laucher smaller, in any easy way. I only have space for 7 applications and my home-folder on my launcher.

PS. If I put system-monitor on the launcher, it's only a symbol. If i add it to the panel, it's show systemsactivity, and if I click it, it's a launcher for system-monitors.

---

### Post by WasMeHere on 2011-11-01
Yes, it's big and the icons are big. And you are correct, it is not a panel (like the gnome panels). But at least it auto-hides, when an application needs the space. I feel like Unity is made for hand-held devices with small screens. But we will probably get used to that kind of desktop interface. And I think that by the time mice belong to history, and we only use fingers on touch screens or voice commands, Unity will fit better than gnome 2 ;-)

---

### Post by Paddy Landau on 2011-11-01
> **Azyx said:**
> You aren't even able to make the laucher smaller, in any easy way.
Open CompizConfig Settings Manager (if you don't have it, install [ccsm]("apt:ccsm")), then select Desktop (on the left) > Ubuntu Unity Plugin > Experimental > Launcher icon size. Modify the size to your preference (minimum size 32 pixels).

---

### Post by Azyx on 2011-11-01
> **Olle Wiklund said:**
> Yes, it's big and the icons are big. And you are correct, it is not a panel (like the gnome panels). But at least it auto-hides, when an application needs the space. I feel like Unity is made for hand-held devices with small screens. But we will probably get used to that kind of desktop interface. And I think that by the time mice belong to history, and we only use fingers on touch screens or voice commands, Unity will fit better than gnome 2 ;-)

I agree. But I think Gnome-fallback are a bit better for me now:) It's slower than Gnome 2, and it being painfull if you don't have new hardware it think, but it's more simulare to 2.  I try it now on a netbook. Have to bee prepared.

---

### Post by Azyx on 2011-11-01
> **mcduck said:**
> Since you asked how to do this in Unity, here's the answer:

Unity uses Zeitgeist to store this kind of history, so you can use tools like Activity Log Manager and Gnome Activity Journal to control what's stored in the history. (I'm not sure if Gnome Shell is currently using Zeitgeist or some other method, but at least it's going to use Zeitgeist in the future)

Gnome Activity Journal is mainly intended for viewing the history, but it also allows you to remove individual items from the journal.

Activity Log Manager gives you more detailed control about what kind of activities are logged, allows you to exclude items from certain directories or of certain file types or based on application used. It also gives you the option to erase history from a certain time range, or from previous 15min/hour/2hours/6hours/day/week.

edit: Both these tools are available from the [Zeitgeist PPA repository]("https://launchpad.net/%7Ezeitgeist/+archive/ppa").

Is there any application I can see the log with? Firefox and log-viewer show all unimportant xml-stuff. 

I have installet zeitgeist on Ubuntu 10.04LTS after added PPA
/Cheers

---

### Post by vasa1 on 2011-11-12
What about BleachBit?

---

### Post by Azyx on 2011-11-12
> **vasa1 said:**
> What about BleachBit?

Will see. Thanx

---

### Post by Azyx on 2011-11-12
> **vasa1 said:**
> What about BleachBit?

Seems only to be able to clear all history :(

---

