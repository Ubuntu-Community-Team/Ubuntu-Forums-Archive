---
title: "Open downloads in FireFox 3"
date: 2009-04-26
forum: General Help
---

### Post by Sciamano on 2009-04-26
Hi!
My Firefox has started acting weird lately.

Scenario: I download a file. The download dialog opens up (Save as / Open with). If I choose 'open with' it will download the file and open it with the associated program (for example, if it's a PDF file, firefox will open the downloaded file with KPDF).

But, if I choose to save the file and then go to the downloads list (Tools -> Downloads) and double click the downloaded file in the list, it will open it with Ark. Whatever the file type is, it will **always** try to open it with Ark.

Anyone has any idea how to solve this?

Thanks!!

---

### Post by Sciamano on 2009-04-27
No one?

---

### Post by kanikilu on 2009-04-27
Have you checked the program association in Firefox (Edit > Preferences > Applications)?

...actually, now that I think about it, when you open a file from the downloads window, I think it takes the system program associations rather than the ones in the Firefox preferences.

I don't use Nautilus anymore, but according to another page, the steps to set the default program are:

* In Nautilus, right click on the file and choose Properties from the menu that appears. The Properties dialog opens.

* Click on the Open With tab. A list of applications appears.

* Select the default application you want for the file type. If the application is not on the list, use the Add button to add the application to the list.

// Edit - Just saw that you specified "All Variants" but I assumed the default Ubuntu (gnome) since you didn't say otherwise...

---

### Post by Sciamano on 2009-04-27
Hi Kanikilu, I don't think this is the problem. In fact, my system opens each file correctly.
But when I try to open them from the downloads list of firefox, it tries to open them all with Ark!

Anyway I'm using Kubuntu, so no Nautilus for me, but Dolphin... maybe I should have specified it in the variants tag. But I don't think the problem is KDE related, that's why I used the All Variants tag...

---

### Post by kanikilu on 2009-04-27
Hmm, I'm not sure then, sorry. I don't use Ark or KDE, so the only thing we have in common is Firefox, and I can't duplicate the problem.

Out of curiosity, did you by any chance double-check the Applications tab in the Firefox preferences?

---

### Post by Sciamano on 2009-04-27
Yes, I did.
The only association that uses Ark is for a generic "file" (check the attached image).
The problem is that I tried to change association (to "Always Ask") and see what happens, but I simply can't: even though I can see different options ("open with" other programs) I can't select them!

---

### Post by kanikilu on 2009-04-27
Strange, I don't have a generic "file" listed in the content types. I don't really see a way to remove content types in Firefox. You said you couldn't change it to something else, but under "Action", can you choose "Application Details" and remove Ark and anything else in there?

Are you maybe using an addon or plugin that might be causing this? Details of your plugins can be viewed by putting the following in the address bar: ```
about:plugins
```

The only other thing I can think of is to try a new Firefox profile. Start Firefox from the command line with the -ProfileManager option to create a new one.

---

### Post by Sciamano on 2009-04-27
I restarted the system (it reminded me of my Windows days!) and then I was able to change the "file" association to "Always Ask".

Seems like this managed to partially solve, since now if I double click on any file in my downloads list, FF will ask for which application to use.

But shouldn't it simply open it with the default app of the system? :confused:

I really would like to find a way to remove that "file" entry, since I'm positive it's the source of the problems. There must be a way to do it without creating a new profile (just the idea of starting again from scratch really makes me sick! :D )

BTW, thanks for your help so far.

---

### Post by Sciamano on 2009-04-27
I removed all listed applications proposed for the "File" association, and now when I click on a download the window I attached opens up.

I think that the origin of the problem might reside in the checkbox I marked in red in the image (I don't remember doing it, but I might have selected it by mistake)...

---

### Post by kanikilu on 2009-04-27
Not sure if this helps or applies, but just came across this thread that sounds similar:

[http://ubuntuforums.org/showthread.php?t=851300](http://ubuntuforums.org/showthread.php?t=851300)

// Edit - It was really bothering me that I couldn't find where Firefox stored content types. The thread linked above pointed me in the right direction: ~/.mozilla/firefox/<random-profile-name>/mimeTypes.rdf - Maybe you can remove the "file" entry from there?

---

### Post by Sciamano on 2009-04-27
Yes, the problem looks like the same. I've tried almost all of the solutions proposed, but nothing helped so far.

Anyway I was now able to reproduce it: when I choose "Remember my choice for file links", FF will use that application to open each and every file from that moment on.

I also tried deleting the mimeTypes.rdf file in the profile folder, but the "file" association is still there... there MUST be a way to get rid of it!

---

### Post by Sciamano on 2009-04-29
Anyone has any clue about how to remove a File Type?

---

### Post by Sciamano on 2009-05-04
up

---

### Post by Sciamano on 2009-05-11
up

---

### Post by Hellion DarkLord on 2009-05-31
you can change the settings using edit>preferences> applications tab

That might help.

Also, when you DL a file open the directory and right click the icon for the file.  Choose properties from the drop-down list.  Then on the general tab there is a button to change the file's application association.  This button allows you to change what application is chosen to open the file.

Good luck that's all I know.

HD

---

### Post by Ms_Angel_D on 2009-05-31
On Kubuntu to make firefox open with dolphin you need to do this:


[LIST=1]
[*]In Firefox go to: Edit -> preferences -> Applications and chose the item 'file'.
[*]Choose Other
[*]Set the Location to /usr/bin/X11/dolphin
[/LIST]

Now it should open with dolphin by defualt.

---

### Post by Sciamano on 2009-06-01
Hi Hellion DarkLord,
thanks for your suggestions, but unfortunately I've already tried that many times with no result.

Hi Ms_Angel_D,
I don't want to open every file with dolphin, I want to open each file with the default system application (a PDF should be opened by KPDF and a tar.gz file should be opened by Ark, for example!).
I can't manage to do that, and I can't seem to find any way to let FF do it.

---

### Post by ythaaa on 2009-07-06
hi i am having the same problem..... exactly the same problem... anyone have any idea to resolve this? thanks

---

### Post by brommage on 2009-08-24
Same problem here also (Kubuntu 9.04 w/ KDE 4.3).  Would love to hear if anyone has found a solution to this peculiar behavior.

---

### Post by Toadicus on 2009-10-22
The same thing happens for me with Firefox 3.5 on the latest Karmic.  It wasn't happening before I upgraded to Karmic, so I thought it was just me.

Choosing to open a file when I click the link works, but the Downloads window interprets all files as "File Link," and asks me how to open them.  if I set "always use XX", it uses that for all files.

---

### Post by pochmann on 2010-07-29
I tried delete ~/.mozilla/firefox/<random-profile-name>/mimeTypes.rdf
didn't work.

so I remove kmozillahelper.

and did the association again.

it works!**

---

### Post by dacman48 on 2010-07-29
in my limited experiance, the red box is what did it

---

