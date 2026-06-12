---
title: "Android UbuntuForums improvement request ... ?"
date: 2020-11-17
forum: Forum Feedback &amp; Help
---

### Post by dbee on 2020-11-17
I've had to avoid using these forums on my android phone. Namely because the UI is completely unituitive IMO. 

Yesterday I was on my phone all day and thought I'd check in on my thread. I logged in no problem. Then i pressed the three dots in the top right-hand-corner. Which brought me to a menu page.

On the menu page was a list of icons including forums, profile etc... So i click *profile* since generally that's where you find a list of your own threads.

But on ubuntuforums it just brings me to a search page. Literally when i press *profile*. The search button at the top of the page highlights. And it's not CLS (Cumulative Layout Shift). This seems to be how the site works.

So then I'm on a search page. I have to scroll down and search for threads by username among the many, many text inputs and drop down menus. Only regardless of the fact that I'm logged in. I can't find my username anywhere. I'm an infrequent UbuntuForums user and I don't know my username off by heart. I have different usernames for nearly every forum. So it's not always obvious.

Then, if i do remember my username. I have to fill out a spam captcha at the bottom of the page to run a search. 

I'm not a UI/UX guy, but I believe this breaks a number of UI design principles and best practices. It's not intuitive and provides a poor UX IMO. 

Can someone do something to fix this pls? It's fine on my laptop.

---

### Post by coffeecat on 2020-11-17
> **dbee said:**
> 
On the menu page was a list of icons including forums, profile etc... So i click *profile* since generally that's where you find a list of your own threads.

But on ubuntuforums it just brings me to a search page. Literally when i press *profile*. The search button at the top of the page highlights. And it's not CLS (Cumulative Layout Shift). This seems to be how the site works.

That's a bug, strangely one that has never been noticed or reported in all the years since the mobile skin was implemented.

If you go back to the three dots menu page, with your phone held in portrait mode, you'll see that the Profile, Messages, and What's New buttons are vertically placed under the search button. Tap any one of them, and you are taken to the search page. That's not meant to happen. Here's a workaround. When on the menu page, simply turn your mobile phone so that you are viewing it in landscape mode, and you'll see that the search button has shifted to the right relative to those other three buttons. The other three now work as they should, but the unoccupied grey area vertically below the search button is still interpreted as the search button itself. 

That obviously needs fixing. I cannot give any promises as to when or if that will be done. Security tightening since a serious forum hack a few years ago, has resulted in it being increasingly difficult for forum admins to - well - administer the forum. I'd better say no more. 

I think your problem with the search page may be down to unfamiliarity with the advanced search utility, which a lot of people have difficulty with, and which is surprisingly powerful once you get to grips with it. I'm feeling too unwell at the moment to look at that part of your post in any detail just now, but I have answered your most important point, which will hopefully obviate the need to search for your own posts from the search page. I'll try to get back to the search page issue in due course.

---

### Post by dbee on 2020-11-17
> **coffeecat said:**
> That's a bug, strangely one that has never been noticed or reported in all the years since the mobile skin was implemented.

If you go back to the three dots menu page, with your phone held in portrait mode, you'll see that the Profile, Messages, and What's New buttons are vertically placed under the search button. Tap any one of them, and you are taken to the search page. That's not meant to happen. Here's a workaround. When on the menu page, simply turn your mobile phone so that you are viewing it in landscape mode, and you'll see that the search button has shifted to the right relative to those other three buttons. The other three now work as they should, but the unoccupied grey area vertically below the search button is still interpreted as the search button itself. 

That obviously needs fixing. I cannot give any promises as to when or if that will be done. Security tightening since a serious forum hack a few years ago, has resulted in it being increasingly difficult for forum admins to - well - administer the forum. I'd better say no more. 

I think your problem with the search page may be down to unfamiliarity with the advanced search utility, which a lot of people have difficulty with, and which is surprisingly powerful once you get to grips with it. I'm feeling too unwell at the moment to look at that part of your post in any detail just now, but I have answered your most important point, which will hopefully obviate the need to search for your own posts from the search page. I'll try to get back to the search page issue in due course.


Thanks coffeecat. I have my phone orientation locked. So i'd have to manually unlock it. Click the *profile* icon. Then lock it again.

It's not an urgent fix though. I guess i can remember my username is *dbee* from now on. Or alternatively, i can click on the *Full Site* link on the bottom of the page. Where it'll be displayed in the header. 

However, it wouldn't be too difficult to display a username on the search page. Maybe even prepopulate the search function with the given username perhaps?

I'm sure vbulletin must have a fix for this issue?

---

### Post by oldfred on 2020-11-17
Search remembers you name. I have oldfred in search & click the exact name button.
[https://ubuntuforums.org/search.php?search_type=1](https://ubuntuforums.org/search.php?search_type=1)
The above is my default Forums page with my login name.
Then I find all threads I have recently posted in. Those with new posts (by anyone) are bold, others are not.

I do not use phone, but above works well in Firefox and used to work in other browsers, but have not tried lately.

---

