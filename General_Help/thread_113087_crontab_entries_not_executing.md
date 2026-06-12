---
title: "crontab entries not executing?"
date: 2006-01-05
forum: General Help
---

### Post by jonathanhayward on 2006-01-05
I have crontab entries as root and as my main account, and neither of them seem to be running, even for entries that should be run each minute. Is there a reason why crontab entries wouldn't be working under Breezie Badger? How can I get cron working?

I was able to create crontab entries without difficulty, via "crontab -e". Is anything else necessary to have the entries be executed?

++ Jonathan Hayward, [email]christos.jonathan.hayward@gmail.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by bored2k on 2006-01-05
Are your user jobs supposed to run certain things as root ? If so, visudo needs to get edited too.

Recommendation: [http://www.gnomefiles.org/app.php?soft_id=148](http://www.gnomefiles.org/app.php?soft_id=148)
[IMG]http://gnome-schedule.sourceforge.net/screenshots/gnome-schedule_main.png[/IMG]

---

### Post by jonathanhayward on 2006-01-05
[QUOTE=bored2k]Are your user jobs supposed to run certain things as root ? If so, visudo needs to get edited too.

Recommendation: [http://www.gnomefiles.org/app.php?soft_id=148](http://www.gnomefiles.org/app.php?soft_id=148)[/QUOTE]

I have user crontab entries which I created under my user account, and root crontab entries which I created as root. Neither seem to be working, and I don't have any user jobs that are supposed to run as root.

I looked briefly at gnomefiles; it looks like a configurator that runs on top of cron, and would not likely work if cron itself doesn't work.

Or does cron work differently from a standard Unix/Linux crontab? Is the format different?

++ Jonathan Hayward, [email]christos.jonathan.hayward@gmail.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by professor_chaos on 2006-01-05
try posting your crontab entries
by executing the command "crontab -l"

---

### Post by jonathanhayward on 2006-01-05
[QUOTE=professor_chaos]try posting your crontab entries
by executing the command "crontab -l"[/QUOTE]

Thanks... as root:

* * * * * start_logisticd

from my user account:

* * * * * test_network 2> /dev/null
* * * * * start_insightd

++ Jonathan Hayward, [email]christos.jonathan.hayward@gmail.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by professor_chaos on 2006-01-05
I have a few suggestions. Actually, I never thought of using the time option of "* * * * *"? Does this mean your executing your cron command every minute of every hour of every day, etc. And is this what you want?

Ok, Did you make sure your program  (ie. start_insightd) is set to executable.
And is it in your path (or roots path). You may want to put the full path to the file.

---

### Post by jonathanhayward on 2006-01-06
[QUOTE=professor_chaos]I have a few suggestions. Actually, I never thought of using the time option of "* * * * *"? Does this mean your executing your cron command every minute of every hour of every day, etc. And is this what you want?

Ok, Did you make sure your program  (ie. start_insightd) is set to executable.
And is it in your path (or roots path). You may want to put the full path to the file.[/QUOTE]

It was a path issue that resolved by my giving a full path. :-)

++ Jonathan Hayward, [email]christos.jonathan.hayward@gmail.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

