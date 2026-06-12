---
title: "unsitall or stop beyrl"
date: 2007-06-20
forum: Desktop Effects &amp; Customization
---

### Post by lilmill on 2007-06-20
I am getting the dreaded WSOD after getting beyrl installed. I see the beryl diamond in the upper left and left screen goes white. Any idea on fixing or how do I uninstall it.

---

### Post by zero244 on 2007-06-20
If your using Ubuntu this will completely remove it.
Copy and paste this in terminal

sudo rm -rf ~/.beryl* ~/.emerald* && sudo dpkg -r --force-depends beryl beryl-core beryl-manager beryl-settings emerald emerald-themes libemeraldengine0

As far as getting beryl to work there are so many varibles. At the moment I have it running just fine. Generally it takes some serious research to find the right How To for your setup.
Its really a pretty impressive bit of code and can work very well for many people.
It can break things and its something that takes a lot of experimentation or trial and error to get it running well.
On my machine it runs very fast and uses very little resources.
If you just went to experiment around give it a try. I wouldnt do it with a computer that has critical data on it, till you figure out if beryl is going to work for you.

---

