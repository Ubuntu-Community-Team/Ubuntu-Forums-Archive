---
title: "Minor Firefox Issue"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Cheesemold on 2006-08-31
This may be posted elsewhere in the forums, but I'm not sure what to call it, the feature that Firefox in Ubuntu seems to be lacking.

This feature that I've become very partial to on my windows machine doesn't seem to be available on Ubuntu.  Being able to use advanced search parameters with Firefox from the address bar, instead of from its designated search field.

Example:  I want to search for food on google, I type "google food". OR: I want to look up the definition of some word, I type "dict exuberance". OR: I want to see what's on wikipedia about linux, I type "wp Linux". Etc, etc

I can do this from Opera, both on the Windows machine, and on Ubuntu.  But, right now, I'm using Opera, and its glorious sessions, for other purposes than general web browsing.  The specific feature does not seem to be mentioned anywhere in the application's settings.  I would like for Firefox to have the functionality it has on my Windows machine, but I simply don't know where to start.

Any advice?

---

### Post by closet geek on 2006-08-31
For some reason the Firefox that comes with Ubuntu doesn't include the handy Quick Search bookmarks feature that Firefox usually comes with. You'll have to manually create each bookmark and assign the %s and shortcut name i.e. google

Look in the Bookmarks of your Windows Firefox, click on the quicksearch bookmark of your choice and study its properties.

cg

---

### Post by df3n5 on 2006-08-31
Are you guys talking about the search bar in the top left where you press the arrow and get a bunch of search engines? Because I have that and it works fine with advanced searches in google and I just installed ubuntu.

---

### Post by Cheesemold on 2006-09-01
Thank You, closet geek, for telling me what it's called.  After a search on google I was able to find out how to get it set up.

Oh, and df3n5, we are not talking about the built in search bar on the **right** side of Firefox.

Since I now know how to do it, I'll explain here.  All one needs to do is create a new bookmark with the URL in the format like this: [http://www.google.com/search?q=%s](http://www.google.com/search?q=%s).  We have an example of how to format the basic google search here.  Note the presence of the %s at the end, where your query would normally go.

To add a Quick Search manually, do this:
1. Go to Bookmarks>Manage Bookmarks...
2. Add a new bookmark by clicking the button in the upper left OR rightclick anywhere in the bookmark listings to add a new one.
3. A new dialog box will pop open. Under Name, put the name of the search engine (or anything you want, really).  Under Location, put the URL with the %s, in google's case: [http://www.google.com/search?q=%s](http://www.google.com/search?q=%s) .  And under Keyword, put the text that you want to type to signify the search you wish to use, such as the letter g.
4. Click 'Okay'.
5. Now, in any random tab, hit Ctrl+L to get keyboard focus on the address bar and type 'g ubuntu', searching google for anything having to do with ubuntu.


See? isn't that so much BETTER than having to click once, look for the search engine you want, click that, and then type?  Now everything's controlled by the keyboard, like it should be.

Oh--One more thing.  You can actually have Firefox do the hard work (URL formatting) for you.  If you're faced with a site that doesn't display immediately what URL you need, Like Ubuntuforums.org, you can have Firefox do that for you.

Here's how:
1. Rightclick in the search field on the site, where you would normally click to enter text.
2. Select 'Add a Keyword for this search' from the rightclick menu.
3. Perform steps 3 through 5 from the other guide, minus having to enter the URL yourself.

It's so easy!

---

