---
title: "Forum changed over Xmas, edit buttons missing"
date: 2021-12-30
forum: Forum Feedback &amp; Help
---

### Post by TheFu on 2021-12-30
Running Firefox v95.0 and all the edit buttons have been removed from regular and advanced reply editor pages. These had been working for a very long time.

Cleared cookies and the cache.  No joy.

Tested with Chromium in a private firejail. The editor buttons are all available. Good.
Tested with Firefox v95 in a private firejail. The editor buttons are all available. Good.

Things that used to work stopped working since last week - I haven't patched due to Xmas holidays, so the exact same programs and settings are being used.  Our network blocks much of google - mostly tracking domains like googletagmanager. It wasn't a problem previously and the blocking hasn't been changed in months.  Is GTM mandated now?

Anyone else noticed that Firefox privacy settings have broken ubuntuforums.org?  That's where I'm currently guessing the issue lies.

Feels odd for me to be posting about missing editor buttons.

Found this: [https://support.google.com/analytics/answer/1009683?hl=en#zippy=%2Cin-this-article](https://support.google.com/analytics/answer/1009683?hl=en#zippy=%2Cin-this-article)  
[https://chrome.google.com/webstore/detail/tag-assistant-legacy-by-g/kejbdjndbnbjgmefkgdddjlbokphdefk](https://chrome.google.com/webstore/detail/tag-assistant-legacy-by-g/kejbdjndbnbjgmefkgdddjlbokphdefk)

---

### Post by &amp;KyT$0P# on 2021-12-30
For me in Firefox 95.0.1 the buttons are all there and seem working, and I didn't have to do anything to make it work now.  GTM is blocked here.  What Firefox extensions are you using?  What Firefox privacy settings changes have you tried?

---

### Post by TheFu on 2021-12-31
> **halogen2 said:**
> For me in Firefox 95.0.1 the buttons are all there and seem working, and I didn't have to do anything to make it work now.  GTM is blocked here.  What Firefox extensions are you using?  What Firefox privacy settings changes have you tried?

Thanks for responding.  Restarting my normal browser, in a normal setup, the way I use it daily, is a huge hassle. There are 20 tabs, lots of logins, so it isn't something easy.
Running the browser in a constrained environment is pretty easy, but any changes to the settings from the defaults are wiped when the browser is restarted.

My addon list is short.
* Wallabagger
* NoScript - by default, I block all Javascript, but here, I allow uf.org. Everything else is blocked.
* TreeStyleTabs
* uBlock Origin

The UF cookies are limited to "Essential".

While creating that list, I see that uBlock has an update. I've applied it, but haven't restarted the browser. In a new tab, it didn't change anything.

Just started a new Incognito/private Window in the browser.  That is showing all the buttons, after login, so it seems clear to be something related to the cache or privacy settings.  From the new FF window, it appears to have inherited the custom privacy settings from the parent, though I have some doubts about that.

Sorry to waste everyone's time.  After a restart, if there is still an issue, I'll see what a new profile under a different user-account does. For now, I can use the Private window.

---

### Post by TheFu on 2022-01-08
So, I rebooted (been a few weks) and the forums still have the same issue.

---

### Post by &amp;KyT$0P# on 2022-01-08
Are any of your extensions not Allowed in Private Windows?
What version of NoScript are you using?
If you open Web Console (Ctrl-Shift-K) on an affected page, any notable messages there?
Any notable blocked/errored requests in Network panel of Firefox devtools?

---

### Post by ajgreeny on 2022-01-09
On the assumption that by "editor buttons" you mean all the icons in the toolbars of the Reply to Thread (or Post Quick Reply) window, I am not seeing this problem either, though I am also on version 95.0.1.

---

### Post by TheFu on 2022-01-09
> **ajgreeny said:**
> On the assumption that by "editor buttons" you mean all the icons in the toolbars of the Reply to Thread (or Post Quick Reply) window, I am not seeing this problem either, though I am also on version 95.0.1.

Good question.

Editor buttons are all the buttons above the reply text entry box.   bold, italics, fonts, and all the the others.   1 line for basic editing and 2 lines for Advanced editing.  The emocons and icons on the right and below are there.

---

### Post by TheFu on 2022-01-09
> **halogen2 said:**
> Are any of your extensions not Allowed in Private Windows?
What version of NoScript are you using?
If you open Web Console (Ctrl-Shift-K) on an affected page, any notable messages there?
Any notable blocked/errored requests in Network panel of Firefox devtools?

NoScript: v11.2.14  I'm not blocking javascript from ubuntuforums.org. All that shows as blocked is googletagmanager.com. That is also blocked by DNS and has been for a few years.  NoScript settings haven't been touched in a very long time.  If a website doesn't work and I **need** access, I usually switch from FF to a firejail --private chromium browser.  Chromium has unfettered access, but forgets everything after every run thanks to firejail.  I'm not using a snap for chomium, since snaps don't work inside firejails.

I'm seeing lots of Content Security Policy errors related to newreply.php.  Interesting.
```

Content Security Policy: The page&#8217;s settings blocked the loading of a resource at data: (&#8220;media-src&#8221;).
Content Security Policy: Couldn&#8217;t process unknown directive &#8216;script-src-attr&#8217;
Content Security Policy: Couldn&#8217;t process unknown directive &#8216;script-src-elem&#8217;
Content Security Policy: Couldn&#8217;t process unknown directive &#8216;script-src-attr&#8217;

```
I haven't changed any of those settings in ... perhaps 2 yrs ... this is an excellent pointer. I've only looked at the browser console in passing a few times, though the Network one is very helpful in using the Copy as cURL for gaining access to less easy content I'd like outside a browser. That's OT.

Loading failed for the ... for some scripts hosted on ubuntuforums.org ... that's likely the issue which goes back to some new content change that breaks a policy.  I'm not against opening the security policies for ubuntuforums.org, if that's possible.  I'll have a look.

Ok, in the enhanced tracking protection, I use "custom settings" and block all 3rd party cookies. Also, block all the other things.  According to Mozilla's support page: [https://support.mozilla.org/en-US/kb/enhanced-tracking-protection-firefox-desktop?as=u&utm_source=inproduct#w_what-to-do-if-a-site-seems-broken](https://support.mozilla.org/en-US/kb/enhanced-tracking-protection-firefox-desktop?as=u&utm_source=inproduct#w_what-to-do-if-a-site-seems-broken) ... there is  a shield next to the URL which allows customizing the stance for every website.  Clicking into that shows the normal No, Enhanced, and Custom Tracking protection page.  It says that there aren't any tracking methods seen, no social networks shown, no 3rd party cookies and no other "tracking content" - - but "enhanced tracking protection" is enabled ... which isn't actually my default setting. 

So, I completely disabled "enhanced tracking protection" and these pages all reloaded immediately, but no buttons are shown.  Pfffft.
Forced a reload - no joy.
Went to a new UF page and manually downloaded some of the javascript 
view-source:[https://ubuntuforums.org/clientscript/vbulletin-editor.js](https://ubuntuforums.org/clientscript/vbulletin-editor.js) works. So does:
view-source:[https://ubuntuforums.org/clientscript/vbulletin_lightbox.js](https://ubuntuforums.org/clientscript/vbulletin_lightbox.js)
Both of those are failing the Content Security Policy.  They are in the cache now, I guess.

Reload the new page and all the buttons show up.  What?
Reload this page and I have buttons again.  Whaaaaaaat?

Certainly there is a bug in FF somewhere. Don't know where.  But it has resolved itself.  I was thinking there was some bad HTML with empty scripts or something like that which was breaking firefox.  BTW, enabled "enhanced tracking protection" for UF and everything is still working. 

I haven't a clue, but not having to enter ** stuff anymore ** manually will be nice.

Solved.

---

