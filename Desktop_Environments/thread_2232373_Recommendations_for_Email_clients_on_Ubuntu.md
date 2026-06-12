---
title: "Recommendations for Email clients on Ubuntu"
date: 2014-07-01
forum: Desktop Environments
---

### Post by vbacon on 2014-07-01
I just switched off of Windows 8 to Ubuntu on my laptop.  So far, I'm loving it!  It's been some work but I've got most of the apps I used on Windows working on Ubuntu.  The one exception is email.

I've got Evolution going but find it buggy.  I can add new folders, but the app crashes every time I do so.  The folders are there when I restart the app, but this is a bit annoying.

Also, very important to me is calendar sync'ing with Gmail.  I have my desktop, iPhone, and work computer all sync'ing with my Gmail calendar which is great.  However, it seems that while Evolution can see my Gmail calendar it can't do a two-way sync.  Any suggestions?

I've used Thunderbird and would consider it here but I found it buggy on my PC.  It would often somehow corrupt the mail file and all messages from before a certain date were unreadable.  I had to develop a vigorous backup strategy.  It was a pain to reload old files.  Also, it looks like Thunderbird on Ubuntu has no calendar.

Thanks!!  This is my first post and I'm happy to be a part of the Ubuntu community.

---

### Post by pfeiffep on 2014-07-01
> Also, very important to me is calendar sync'ing with Gmail. I have my desktop, iPhone, and work computer all sync'ing with my Gmail calendar which is great. However, it seems that while Evolution can see my Gmail calendar it can't do a two-way sync. Any suggestions?

I use 2 Linux computers one of which has Win 7 dual booting. I also have an iPhone and find the Thunderbird will satisfy your requirements.:p

---

### Post by kurt18947 on 2014-07-01
> **pfeiffep said:**
> I use 2 Linux computers one of which has Win 7 dual booting. I also have an iPhone and find the Thunderbird will satisfy your requirements.:p

+1 on Thunderbird.  I believe (though I don't use google so not certain) that the lightning add-on for Thunderbird will sync with Google Calendar.  I've had no corruption issues and recent iterations of Thunderbird have settings for major email providers already included so there's a good chance that when you enter your email address, the server settings will already be known.

---

### Post by r_avital on 2014-07-01
Hi vbacon,

Has it been a while since you've used Thunderbird and had issues with it?  If so, I'd recommend another look, it's been very stable for me and for many others.

Regarding Google calendars, that is definitely supported in Thunderbird, you just need to make sure that you install the necessary packages.  Specifically:
xul-ext-lightning
xul-ext-gdata-provider
xul-ext-calendar-timezones

Don't take my word for it, but I believe they're automatically marked for installation when you install Thunderbird.  It also has a very good interface to GPG for encryption (GPG is installed by default in Ubuntu), through the package called "enigmail."

Lastly, the best thing that happened to Thunderbird is that the maker, Mozilla, has stopped updating it every 15 minutes (except for security updates which afaik are still provided).

If you end up using Thunderbird, don't necessarily mean you should uninstall evolution, because together with a Thunderbird addon/extension, you can have changes in your Gmail calendar that are shown in Thunderbird get reflected in the gnome calendar applet(on the top panel) but that requires evolution being installed.  That's a minor convenience, though, and it's entirely up to you.

---

### Post by amanchesterman on 2014-07-02
I can confirm that Thunderbird, with the Lightning calendar add-on, syncs smoothly with Gmail calendar: I currently have it running on Xubuntu 14.04, and I have used it on previous versions over the last two years. (Xubuntu in my case because my laptop runs slowly with Ubuntu).

With respect, I think that r_avital is incorrect in saying that Lightning installs automatically with Thunderbird. But if you install TBird from the Software Center, it's listed there as an option, along with the Google calendar provider extension that you will need.

If you use Google Tasks to manage your to-dos, there's an extension that lets you sync with that too, but you have to download that from the Thunderbird extensions website.

---

### Post by vbacon on 2014-07-02
Thanks for the replies!  I will give Thunderbird a try.  The last time I used it was on a Windows machine and that was a while ago.

I'm really disappointed with Evolution.  Again today I spent most of my 40 minute train ride dealing with its eccentricities as opposed to dealing with emails.  :(  Today it showed no email in a folder I just put a couple of emails in.  It appeared they and a few in some other folders were now altogether lost.  Then, a few minutes later they were all there.

---

### Post by aramil248 on 2014-07-02
Thunderbird is great i used it in xubuntu 12.04 and when i upgraded to lubuntu 14.04 i installed it because the email client that installs with lubuntu is confusing to use

---

### Post by kurt18947 on 2014-07-03
> **vbacon said:**
> Thanks for the replies!  I will give Thunderbird a try.  The last time I used it was on a Windows machine and that was a while ago.

I'm really disappointed with Evolution.  Again today I spent most of my 40 minute train ride dealing with its eccentricities as opposed to dealing with emails.  :(  Today it showed no email in a folder I just put a couple of emails in.  It appeared they and a few in some other folders were now altogether lost.  Then, a few minutes later they were all there.

Don't feel alone.  I tried Evolution and had little success with it.  If I had taken the time perhaps I could have made peace with it but when Thunderbird was a few clicks away I didn't feel the need.

---

### Post by JohnnyComeL8ly on 2014-07-06
> **aramil248 said:**
> Thunderbird is great i used it in xubuntu 12.04 and when i upgraded to lubuntu 14.04 i installed it because [COLOR=#ff0000]the email client that installs with lubuntu is confusing to use[/COLOR]

  I second that thought.

---

### Post by Gordonbp531 on 2014-07-08
When you go to add your Google Calendar, don't bother with the Google Calendar Provider - use CalDav instead.
The URL for your CalDav calendar is https://apidata.googleusercontent.com/caldav/v2/{Your Gmail address here}/events

---

### Post by pfeiffep on 2014-07-09
Another possibility is Google Calendar Tab ... I've been really satisfied with it!

---

### Post by BBQdave on 2014-07-09
Joining the *love fest* with Thunderbird, great email client.

I like the combination of Thunderbird with email accounts geared for email client applications, and Gmail accessed with Firefox Web Browser.

---

### Post by JohnnyComeL8ly on 2014-07-21
> **BBQdave said:**
> Joining the *love fest* with Thunderbird, great email client.

:lolflag:

---

