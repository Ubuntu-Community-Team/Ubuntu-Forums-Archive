---
title: "gstreamer0.8-mad not in my installation !"
date: 2006-04-26
forum: Desktop Environments
---

### Post by susiriss on 2006-04-26
Dear friends,
         According to instructions, **gstreamer0.8-mad **must be installed in my system in order to play MP3 audio. Howewer I enabled **multiverse** and still found that there is no gstreamer0.8-mad listed in the Synaptic package manager. 
                  I installed Ubuntu from the CD shipped to me. Doesn't that package come default with that CD? Will I be able to install it after downloading from the Web? 

Need your help
Thank you.

susiriss

---

### Post by Ramses de Norre on 2006-04-26
It is in universe, enable universe and do sudo apt-get update && sudo apt-get install gstreamer0.8-mad

---

### Post by mjm115 on 2006-04-26
That's because g-streamer0.8-mad is in the universe repository.  I'm sure if you enable that you will be able to find it.

---

### Post by susiriss on 2006-04-26
Friends

I have enabled all of them. And changed the "section" from **universe** to **universe multiverse **in Synaptic Package Manager. What are the other problems?

---

### Post by Ramses de Norre on 2006-04-26
Did you run sudo apt-get update? (or refresh or something in synaptic)
What's the error you're getting? Can you try with apt-get, you might get a more detailed error.
Can you post your /etc/apt/sources.list file?

---

### Post by susiriss on 2006-04-26
Yes I did refreshed the list in the Synaptic. I've got three errors saying something like it can't access the URLs. I will send my sources.list file.

---

### Post by Ramses de Norre on 2006-04-26
It's the easiest when you copy the whole error message too. 
Btw: you are sure you're internet is working perfect?

---

### Post by susiriss on 2006-04-27
Well, 
             As Ramses noted, I think I've got the problem. Initially I thought that those repositories are in the CD. The Error indicates the connection problem to ubuntu site. I have **no internet connection **to my PC where Ubuntu is.
                 Is it possible to **download the repository **and install it? If so, please show me the steps. I'm a novice to the Linux world.

Thanks,
susiriss.

---

### Post by JohnnyMarr on 2006-04-27
try going to [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper) its a very good, very simple and easy to use set of instructions on getting dapper up to user standard, read the repo section on how to manualy change the repos. its alot easier than using synaptic, oh and has a list of all the repos u will need.

EDIT: sry that link was for the dapper version heres the link for the breezy version [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

