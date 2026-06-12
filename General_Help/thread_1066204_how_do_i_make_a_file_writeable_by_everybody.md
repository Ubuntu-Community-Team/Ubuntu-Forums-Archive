---
title: "how do i make a file writeable by everybody?"
date: 2009-02-10
forum: General Help
---

### Post by meself on 2009-02-10
hi.

i am tying to add a new default search engine, [www.AllTheWeb.com](www.AllTheWeb.com), to the search box in firefox 3.0.5. this is the seach box that appears next to the url address box in the tool bar. but it cannot be added by by clicking the searchbox dropdown and then clicking on "manage search engines" and then clicking "get more search engines". so i went to the [http://www.alltheweb.com/help/tools/mozilla](http://www.alltheweb.com/help/tools/mozilla) page and there is a section called "Add AllTheWeb to Internet Search". but it doesn't work. I get the error message "Firefox could not download the plugin". And there is this notation on the section:
NOTE: This feature may not work with Mozilla on Linux. The workaround is to make /usr/lib/mozilla/searchplugins (or /usr/search/mozilla-[version]/searchplugins) writeable by everyone or make it owned by the user running the browser.

Question:
how does one locate the specified file. and then how does one make it wrtieable by everyone?

---

### Post by hikaricore on 2009-02-10
You've made 3 copies of this thread.

Stop it...

---

### Post by meself on 2009-02-10
sorry, i forgot to make the first one subscribed.  and wasn't sure how to get back to it later.  tried to delete the text but couldn't delete the subject.  then i couldn't find the second one.

but i will be more careful about that in the future.  i appologize for the confusion.  won't do it again.

---

### Post by meself on 2009-02-10
the other two copies of this post that i made, and should not have, seem to have been deleted.  so if anybody seems to have any idea how to make a file writeable by everybody, help here would be appreciated.

best wishes,
mike.

---

### Post by snova on 2009-02-10
Press Alt-F2, type in:

```
gksudo nautilus
```

And a file manager with full administrative rights will be started.

Navigate to **/usr/lib/mozilla**.

The **searchplugins** directory doesn't seem to exist in a default installation, so first create it.

Then right-click on it, Properties, Permissions tab. Under 'Others', click the 'Folder access' menu, and select 'Create and delete files'.

It might work, and it might not...

---

### Post by meself on 2009-02-11
thank you snova.  that was helpfu.  unfortunately, it turns out that there is a problem at the [www.AllTheWeb.com](www.AllTheWeb.com) website due to re-organization of the web pages.  the plugin is not located at the download link address.  and the same problem occurs trying to add [www.AllTheWeb.com](www.AllTheWeb.com) as a search to firefox while running under windows xp.  i have sent AllTheWeb a bug report.  but thank you again and your recomendation will be useful if and when AllTheWeb makes the search plugin available again.

---

### Post by meself on 2009-02-11
thank you again for your help.  i have now located the firefox search plugin for [www.AllTheWeb.com](www.AllTheWeb.com) at the following link and it's the fourth one on the list.  works just fine.

[http://mycroft.mozdev.org/search-engines.html?name=ALLTHEWEB](http://mycroft.mozdev.org/search-engines.html?name=ALLTHEWEB)

---

