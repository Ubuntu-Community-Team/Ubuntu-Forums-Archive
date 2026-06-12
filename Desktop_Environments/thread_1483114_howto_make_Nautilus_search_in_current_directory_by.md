---
title: "howto make Nautilus search in current directory by default"
date: 2010-05-14
forum: Desktop Environments
---

### Post by yesplease on 2010-05-14
I work on Ubuntu 10.04 with Gnome.

When I open a directory, I can search with Ctrl-f (edited Ctrl-F instead of F3). However, the search starts in my home directory (the home directory is the default). That can be fixed by adding new criteria in the search results. However, I would like to change the default directory always to the directory or folder from which I start the search.

How can I convince Nautilus to search by default for files and folder names in the current directory or folder (the one from which I start searching)?

---

### Post by labinnsw on 2010-05-15
I suspect you made some preferences edit to be able to search with F3. F3 only splits the nautilus view on my system.

To search a specified directory, what I do is click the search tool icon on the tool bar. A window then opens to accept my search term and the search is done in the current directory. If I want to change  the directory, I have to do so after initiating the search. Just right of the side bar, change the criterion to location and just right of that, select the directory to search.

There are other ways to search, but that is how I do it if nautilus is already up and running.

---

### Post by yesplease on 2010-05-16
"I suspect you made some preferences edit to be able to search with F3. F3 only splits the nautilus view on my system."

That should be Ctrl-f. Sorry to complicate matters.

"To search a specified directory, what I do is click the search tool icon on the tool bar. A window then opens to accept my search term and the search is done in the current directory. "

That seems logical and it is what I would like search to do. Where should I start to achieve this?

---

### Post by 1John on 2010-05-26
I am also experiencing this problem.

I have recently upgraded 2 different machines to 10.4. On these machines before upgrade nautilus searched the current directory by default when I clicked the search icon but after upgrade the home directory was searched which is much slower and more clumsy. 

On one machine I just removed some old 'tracker' files using synaptic and reinstalled nautilus. This fixed the problem. However on the other machine there are no tracker files to remove and reinstalling nautilus has not fixed the problem.

Perhaps the first solution will help you, otherwise we will need to wait for a post from someone who has a bit more knowledge than me.

---

### Post by yesplease on 2010-06-02
Thanks for the answer, but it seems I have no old tracker files on my computer either.

---

### Post by peertje888 on 2010-07-22
Hi there, I've also upgraded to Lynx with my Laptop and can't search either...not even in my home folder. I tried to reinstall it but without any luck. Even Dolphin didn't do the trick for me...

What is this tracker files you are talking about and where can I find them?

Tnx

---

### Post by 1John on 2010-07-26
Hi peertje888. Tracker used to be part of the standard install for Ubuntu but isn't now so unless you have upgraded from 2 or 3 versions ago (Gutsy I think) then you won't have it on your system. If you search on these forums you can find out when and why it was dropped.

To overcome my problem I have now got Beagle installed as I could wait no longer wait for an answer. Beagle does not search a specific directory but is fast and convenient to use once the initial indexing is completed.

---

### Post by peertje888 on 2010-09-09
I figured out that using the "Search for files" option from the "Places" menu did work!

---

### Post by 1John on 2010-09-09
Yep, this works for me too. How did I miss that! Thanks.

Unfortunately the option to search for particular text does not work within open office documents though.

---

