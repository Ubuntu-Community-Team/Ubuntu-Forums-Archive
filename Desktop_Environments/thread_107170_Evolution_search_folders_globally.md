---
title: "Evolution: search folders globally"
date: 2005-12-22
forum: Desktop Environments
---

### Post by dpm on 2005-12-22
Hi all,

I'm completely new to Evolution and I'm struggling with a very basic task: I cannot get "search folders" to work.

I get all my mail delivered to the main inbox from a single pop3 account, from which the messages are then redirected following rules defined in a few filters I've set up. 

There are 3 subfolders where the messages are moved to, each one with some subfolders. So far so good, the filters work without problems. That's more or less what it looks like:

Inbox [POP3 account]

GMX [Local folder, top folder]
>Personal [Local folder, subfolder of GMX]
>>SomeOtherRandomSubfolder [Local folder, subfolder of Personal]

Hotmail [Local folder, top folder]
>Holidays [Local folder, subfolder of Hotmail]
>>SomeOtherRandomSubfolder [Local folder, subfolder of Holidays]

My problem starts when I'm trying to set up a "search folder". I want this search folder to scan ALL of my folders and find all messages with a certain word in its subject. Therefore, I set up the "Search Folder" as follows: IF-> Subject contains "my search word"; SEARCH FOLDER SOURCES->with all local folders. Let me stress that: I do not specify any particular folders there because I'm assuming Evolution is goint to search all folders and subfolders.

That does not return any results, although I do have some messages with "my search word" in the subject in my inbox. However, what I find most strange is that the "Unmatched" folder contains a few results, mostly from a particular subfolder.

I've googled a bit on this, but so far I've had no luck. I find the search and "search folders" features of Evolution a bit confusing. I simply want to find a particular message without having to manually scan every single folder with the search option from the toolbar. Is that possible?

Thanks in advance.

---

### Post by dcstar on 2005-12-22
[QUOTE=desp]Hi all,

I'm completely new to Evolution and I'm struggling with a very basic task: I cannot get "search folders" to work.
.....
I've googled a bit on this, but so far I've had no luck. I find the search and "search folders" features of Evolution a bit confusing. I simply want to find a particular message without having to manually scan every single folder with the search option from the toolbar. Is that possible?

Thanks in advance.[/QUOTE]
Try: Search-Edit Saved Searches-Add and put in your search criteria.

I did this the other day to find messages from a couple of people and it seemed to work (on all my folders).

---

### Post by dpm on 2005-12-23
[quote=dcstar]Try: Search-Edit Saved Searches-Add and put in your search criteria.

I did this the other day to find messages from a couple of people and it seemed to work (on all my folders).[/quote] 
Thanks for your reply. I had already put a search criteria, there was no need to edit it. That's from my original message:

> Therefore, I set up the "Search Folder" as follows: IF-> Subject contains "my search word"; SEARCH FOLDER SOURCES->with all local folders. 
However, I gave your suggestion a shot. Again, I typed in the search criteria (same as before), but that did not change anything.

A minute later, I found out what was wrong: _*Execute Actions*_ was set to *_If **any** criteria are met_*. I changed that to *_If **all** criteria are met_* and now it seems to (kind of) work most of the time. I say most of the time because every now and then my search folders appear to be empty, and they are only populated again if I restart Evolution. Re-applying the search does not help.

That is kind of annoying, but I can live with it. 

Anyway, just another question: are *Serch Folders* the standard way of searching for messages globally in Evolution, or is there another way? It's just that I'm not used to it, but I'm getting there...

Thanks again for any comments.

---

### Post by uglowp on 2007-11-02
I can't get them to work either.

Must be something I am doing wrong but have not been able to figure it out.

---

