---
title: "QuoteZilla (Ubuntu mod) - easily save and post forum quotes"
date: 2009-04-01
forum: Forum Feedback &amp; Help
---

### Post by lovinglinux on 2009-04-01
I was annoyed with the fact that so many people does not use the search feature before posting and with the amount of time spent answering the same questions over and over, so decided to search a way to manage quotes from recurring threads.

[QuoteZilla]("https://addons.mozilla.org/en-US/firefox/addon/8856") is a nice extension for Firefox that can do this. Unfortunately, QuoteZilla output is too generic and not formatted for Ubuntu forums. So I edited a file in the extension, to make it Ubuntu friendly. I will not release a new version for QuoteZilla, because I'm not the author and I don't want to hijack the extension from the developer, but I have attached the modified file in this post. All you have to do is replace the "*QuoteZilla.object.js*" file in the extension folder ( ~/.mozilla/firefox/***.default**/extensions/quotezilla@wing.god/content/QuoteZilla.object.js ) with the one inside the attached gz package.

[Download](http://fmc.isgreat.org/index.php?option=com_phocadownload&view=category&id=3%3Autilities&download=4%3Aquotezilla&Itemid=1&lang=en)

To use the modified version, follow these steps:

1 - To save a quote, simply select the text from a post, right-click it and select the option "*QuoteZilla this*" from the context menu.
2 - Fill the quote author field in QuoteZilla the side bar
3 - Edit the Source link, leaving only the thread number. For example if the Source field is ***[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)***, then delete the forum string, leaving only ***1044714*** and save it. If you don't do this, the quoted text will be messed up.

To post a quote, open "QuoteZilla" sidebar, click the clipboard icon in the quote you want to copy and paste in the post.

---

