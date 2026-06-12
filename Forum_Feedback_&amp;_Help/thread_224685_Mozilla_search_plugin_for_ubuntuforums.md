---
title: "Mozilla search plugin for ubuntuforums"
date: 2006-07-28
forum: Forum Feedback &amp; Help
---

### Post by costoa on 2006-07-28
Here's a search plugin to search ubuntuforums via your firefox search box. The added benefit is that it should take a bit of the load off the ubuntuforums server(s). BTW, I can clean it up if desired. 


1. Create a new text file named "ubuntuforums.src"
2. Add the follow:

```

# Mozilla search plugin for ubuntuforums.org

<search 
   name="Ubuntuforums"
   description="Ubuntuforums search via Google"
   method="GET"
   action="http://www.google.com/search"
>

<input name="q" user >
<input name="q" value="site:ubuntuforums.org/archive">


</search>
```

3. Save in ~/.mozilla/firefox/*.default/searchplugins
4. Restart firefox.

BTW, if you want an icon:
```

cd ~/.mozilla/firefox/*.default/searchplugins
wget http://www.ubuntuforums.org/images/statusicon/forum_new.gif
mv forum_new.gif ubuntuforums.gif

```


In case anyone is interested in an easy installation method:

1. Dump the following into a file called "install-uf-search-plugin.js":

```
function addEngine()
{
    if ((typeof window.sidebar == "object") && (typeof window.sidebar.addSearchEngine == "function")) { 
        window.sidebar.addSearchEngine(
            "http://ubuntuforums.org/ubuntuforums-google-search.src",
        );
    } else {
        alert("Sorry, you need a Mozilla-based browser to install a search plugin.");
    }

```

2. Add the following to your page head:
```
<script src="install-uf-search-plugin.js" type="text/javascript"></script>
```
and the following to the body:
```
<a href="javascript:addEngine()">Add ubuntuforums to your search box</a>
```

I'm sure the js has issues and hasn't been tested. The search part works well but should have an expiration date to allow for updates.

---

### Post by Zelut on 2006-07-28
Hey looks like a cool idea.  I always wondered why there wasn't something like that available.  I'll check it out.

---

### Post by costoa on 2006-07-28
Thanks. BTW, I miss the view of the Timps from your part of the world. I use to live and work in the busy metropolis of Payson. =)

---

### Post by Zelut on 2006-07-28
It really is a thriving metropolis isn't it :)
Too bad you're not around anymore.  We could use more good people on the Ubuntu-Utah Local Team.  Spreadin' the Linux love all over the state.

---

### Post by kwaanens on 2006-07-28
In stead of those steps, you could go [here]("http://mycroft.mozdev.org/download.html?name=ubuntuforums&sherlock=yes&opensearch=&submitform=Search").
Been available for a long time!

Also: [This one]("https://addons.mozilla.org/firefox/2302/") might be interesting.

- Ketil

---

### Post by costoa on 2006-07-28
(Concerning the 1st link) It seems the search plugin link is dead. A bunch of other search plugin links are also dead so I wonder if mycoft is having problems.

Updated: 2006-07-30 1444
It seems to be up. Difference between the two: mine uses google and the other is direct. The direct one will give much more up to date results but put the heavier load on the server. The question for the admins is which is better for them? Is the ubuntuforums server(s) running hot most of the time or can it handle more direct search searches?

BTW, here's the [code]("http://mycroft.mozdev.org/install.php/7130/ubuntuforums.src") . Thanks to Luca Gasperini for doing it.

---

