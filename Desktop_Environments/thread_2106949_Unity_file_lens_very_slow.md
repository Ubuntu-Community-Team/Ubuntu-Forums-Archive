---
title: "Unity file lens very slow"
date: 2013-01-20
forum: Desktop Environments
---

### Post by shof2k on 2013-01-20
Hello,
I've been running 12.04 for a while now, and noticed the unity file lens had become very slow. Getting results for a file search was taking over 2 mins.

Having a hunch, I ran a sqlite clean up on the zeitgeist database and it returned back to its speedy self.

The command being
```

cd .local/share/zeitgeist/
sqlite3 activity.sqlite vacuum

```

Hope that helps.

---

### Post by madhangc on 2013-07-01
Thanks [**[COLOR=#000000]shof2k[/COLOR]**]("http://ubuntuforums.org/member.php?u=13389"), for your sharing. That did the trick :-)

---

