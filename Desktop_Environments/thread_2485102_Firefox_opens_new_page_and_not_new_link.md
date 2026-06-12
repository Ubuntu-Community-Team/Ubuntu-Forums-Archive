---
title: "Firefox opens new page and not new link"
date: 2023-03-20
forum: Desktop Environments
---

### Post by skywalker007 on 2023-03-20
Hi, new to ubuntu. Installed 22.10
When I open firefox, and click on a link. sometimes it will open in a new link but sometimes in a new page.. even if I ask for a new link. Then after a while I obviously have multiple firefox pages open as I get a new page every now and then. I have tried to find things out but people just mention it as a "overflow". I have no idea how to get this fixed. This differs between EXPLORER and FIREFOX, where one choose a new window and another a new tab.

---

### Post by Holger_Gehrke on 2023-03-20
Not much you can do about it. Whether a link you click on opens in the same tab/window or a new one is controlled in HTML by the target-attribute of the a-tag which is how a link is written in html. For example
```

<a href="https://duckduckgo.com" **target="_blank"**>search with duckduckgo</a>

```
will open a new tab with DuckDuckGo while
```

<a href="https://duckduckgo.com" **target="_self"**>search with duckduckgo</a>

```
will take you to DuckDuckGo in the same tab/window. Without looking at the source of the page it's impossible to tell links with different target-attributes apart unless the author of the page explicitly marks them. Different pages have different rules about how links are opened, but in general links on the same server will most likely open in the same tab while links to other server will often have 'target="_blank"'.

Holger

---

### Post by skywalker007 on 2023-03-20
Well, if this is something written in the code that cannot be changed then why if I am using windows EXPLORER and go to google and search for gmail and click on the gmail link.... it opens in a NEW TAB but if I am in ubuntu using FIREFOX and do the exact same thing... it opens in a NEW WINDOW.

As I have only started using Linux now I have seen it in multiple links and that never happened to me when I was using windows. 
I have both operating systems running on the laptop and I actually checked it using more than one page where it happens and all of them WINDOWS EXPORER went to a NEW LINK and FIREFOX (even if I say open in new link), opens a new WINDOW?

---

### Post by Holger_Gehrke on 2023-03-20
Well, now that you're using the same terminology as me I can understand your problem ;)

Have you checked "Settings" -> "General" -> "Tabs" whether "Open Links in new tabs instead of new windows" is active (not sure about the exact words, I'm translating from German ...) ? That should be the default but what you describe is the behaviour you get when that option is off.

Holger

---

### Post by coffeecat on 2023-03-20
> **skywalker007 said:**
>  if I am in ubuntu using FIREFOX and do the exact same thing... it opens in a NEW WINDOW.


Nothing to do with Ubuntu. The default in Firefox in Ubuntu is to open in a new tab, not a new window.  You must have changed your Firefox settings. To change back, click on the hamburger lines top right of your Firefox window -> Settings -> General. Under the tabs heading tick "Open links in tabs instead of new windows". It is ticked by default. 

By the way, I've removed the bold code tags from your post. Please do not post in all bold - it looks as though you are shouting, as do the many words you have written in all caps.

---

### Post by skywalker007 on 2023-03-20
And yes, I did check it and indeed it is set to TABS, and that is the way it always was. And the main reason I am asking is that if I am on the internet, some of the links I click go to new tabs and about 30% of the links go to new windows? For instance the one that I explained that went from gmail in google.

I did try to find out about this and on one page the person just said (it was unfortunately not a group where I could ask) it is a "buffer overflow". I am not sure what he meant by that, and if it is the truth, how do you fix it. It is not a very new laptop but does have 8G ram and 1 TB SDD.

---

### Post by Holger_Gehrke on 2023-03-20
A "buffer overflow" is a type of programming error. You allocate some memory to take data but there's more data then you allocated memory for; then the data will be written beyond the allocated area. If it tries to write into memory the program doesn't own, that's a "page fault" and the program is forcibly ended by the OS - it crashes. If there's memory after the buffer that the program owns, it's content will be overwritten leading to erratic behaviour by the program - and no, I can't be more specific than that, it depends on the data that gets overwritten. If this was the source of your problem, then - unless you're a programmer and very good at debugging memory issues - there's not much you can do about it.

What I'd try to see if it's a problem with Firefox or with your settings is to set up a new profile with none of your settings, extensions or bookmarks. If FF behaves just as badly with the new profile as with the old, then it's a problem in FF and you should report it as a bug to the developers. If it doesn't there's some setting (doesn't need to be one in the menu, there's a lot of settings hidden away in 'about:config') or an extension that's producing the behaviour you see. To create a new profile you can call Firefox from the command line with 'firefox --ProfileManager' and use the profile manager to create a new profile. Alternatively you can move the directory where FF stores all profiles to another name. That directory is ~/.mozilla/firefox for firefox installed from a deb package or from the tarball from mozilla.org or ~/snap/firefox/common/.mozilla/firefox for Firefox installed as snap (default on newer versions of Ubuntu).

Holger

---

### Post by skywalker007 on 2023-03-20
Well, after trying it as well I decided to take a easier way out and just moved over to chrome, it does not appear to have the same problem.
Anyway, thanks for the time and the feedback):P

---

