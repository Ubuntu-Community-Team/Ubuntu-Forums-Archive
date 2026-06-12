---
title: "swap file overkill?"
date: 2009-04-21
forum: General Help
---

### Post by freakbofo on 2009-04-21
Hey there
I was just wondering i installed ubuntu the other week,but about a week before hand i had upgraded my ram to try and get some speed out of my windows vista laptop.Now it seems unnecessary as mp pc flies now.
Anyway i have 3 gb of ram and now it seems i have a 4.6 gb page file?is this overkill?Should i try and change it somehow or am i better off just leaving it how it is.....

thanks for your reply

---

### Post by codeseer on 2009-04-21
That's OK, as long as you don't need that space for something. Generally you should allocate a swap file that is equal in size to the amount of RAM you have.

---

### Post by freakbofo on 2009-04-21
thanks very much,i didnt wanna have to fiddle around to change it anyway....
thanks

---

### Post by zigx on 2009-04-21
freakbofo you might want to check out this article:
[https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27](https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27)

---

### Post by freakbofo on 2009-04-21
Well i have had a look,i am not sure if i would need to do that as i havent touched my page file as yet, its just empty?Following the article is says a "swappiness" of 10 is good,but if the swappiness text doesnt exist in the syctl.conf text i can just paste it in at the bottom.Have i understood correctly?
thanks for your reply !!!!!!!!

---

### Post by zigx on 2009-04-21
Yep, you got it!

Just like they say: 
[INDENT]Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:

vm.swappiness=10[/INDENT]

I have my swappiness @ 10 and i will eventually put it to almost 0 i think.

My desktop machine has 4gigs of ram and it makes no sense to swap when i can just keep it oh so sweet fast ram :)

I think that if this setting works out i might resize my swap partition and reclaim some diskspace too!


sorry but here is yet another link with some interesting comments: [http://brainstorm.ubuntu.com/idea/5481/](http://brainstorm.ubuntu.com/idea/5481/)

---

### Post by freakbofo on 2009-04-22
thanks very much for your help.
information willingly provided like this is making my transition to ubuntu so much easier than i ever thought it would be!!!
thanks very much

---

