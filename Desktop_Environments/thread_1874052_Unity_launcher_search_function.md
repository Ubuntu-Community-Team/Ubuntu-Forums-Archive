---
title: "Unity launcher search function"
date: 2011-11-02
forum: Desktop Environments
---

### Post by JHorrocks on 2011-11-02
Am I missing something, going crazy or just stupid.

Using the new 11.10 unity environment, and clicking the "Super Key" to show the launcher search textbox, why can I not search typing the name of any file that exists in my home folder?

Example: Go to home folder, create a doc called "TEST" and then click the super key and search for the phrase "TEST" it doesnt show.

What the launcher search function is good at doing is displaying anything from my porn collection in my videos folder but nothing from my documents or home folder....

Does this mean Ubuntu 11.10 is a pervert? (or maybe just me)

No seriously, any new doc that I create in any folder up from the /home/user/ folder doesnt show, but music and videos do when you search for them.

Any info would be greatly appreciated..

James..

---

### Post by stinkeye on 2011-11-02
Zeitgeist keeps track of activities on your
 system (file usage, browser history, calendar events, etc.)
Its not really a pure search tool.

If you open that file you just created it will then show up.

You can customize what it logs using [**_[COLOR="DarkRed"]Activity Log Manager for Zeitgeist[/COLOR]_**]("http://www.omgubuntu.co.uk/2011/05/activity-log-manager-for-zeitgeist-lets-you-blacklist-files-and-apps-delete-your-history-more/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29")

---

### Post by JHorrocks on 2011-11-02
Ok, thanks for the link etc, but this looks like it wont solve the issue.

I dont need to install any new software to search for files, I am just curious why the unity launcher doesnt find the files.

------------------------------------------
edited:

Ok I just found out what the issue is...

Because this is a fresh install of 11.10 I copy/pasted all my "existing" files from an external drive into the "Documents" folder. If I open any of the documents and make a change to them then save, they will then show up in the launcher search function.

So, it looks like it is saving a list of docs in a cache or something, so how do I reset this so that it rescans all my existing docs?

---

### Post by stinkeye on 2011-11-02
> **JHorrocks said:**
> Ok, thanks for the link etc, but this looks like it wont solve the issue.

I dont need to install any new software to search for files, I am just curious why the unity launcher doesnt find the files.

------------------------------------------[COLOR="Red"][/COLOR]
edited:

Ok I just found out what the issue is...

Because this is a fresh install of 11.10 I copy/pasted all my "existing" files from an external drive into the "Documents" folder. If I open any of the documents and make a change to them then save, they will then show up in the launcher search function.

So, it looks like it is saving a list of docs in a cache or something, so how do I reset this so that it rescans all my existing docs?

Zeitgeist is a data engine for the GNOME desktop. It **logs and tags** every document, website, conversation, email, note and application that&#8217;s **[COLOR="Red"]opened[/COLOR]** on the GNOME desktop.
PS The link I gave you isn't to install any new software to search for files, it's a tool to
manage Zeitgeist.
Zeitgeist is what the dash uses.

---

