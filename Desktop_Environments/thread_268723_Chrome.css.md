---
title: "Chrome.css"
date: 2006-09-30
forum: Desktop Environments
---

### Post by khulbert on 2006-09-30
I am using a dark theme for GNOME which I absolutely love.  Unfortunately it appears that firefox imports the gtk+ settings for the theme [like so]("http://www.kylehulbert.com/gtkproblem.jpg").  I find this very annoying as it disrupts the flow of many web sites and also renders many textboxes unreadable if the site sets a light color for text boxes.  I was wondering if there was a way to modify chrome.css to fix this problem.  I have never modified this file before so please explain things as completely as possible.  If I am going down a completely wrong track please let me know.  Thanks in advance.

---

### Post by chavo on 2006-09-30
You can install the stylish extension. With stylish you can have a separate style sheet for your dark theme and your light themes and then just turn it on and off. The syntax is exactly the same as user_chrome.css and you can use stylish to create it. Much easier than mucking around with user_chrome.css and having to change it when you change gtk themes. Plus you don't have to restart the browser for the changes to get picked up.

---

### Post by aysiu on 2006-09-30
I don't know much about Chrome.css, but do you have a Firefox theme installed and it still inherits GTK+ settings?

---

