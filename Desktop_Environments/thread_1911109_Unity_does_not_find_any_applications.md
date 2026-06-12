---
title: "Unity does not find any applications"
date: 2012-01-18
forum: Desktop Environments
---

### Post by creiss on 2012-01-18
Hey all,

for some odd reason unity does not find any programs anymore.
If i press the Unity button / superkey, I see the pinned applications like firefox. If i search for firefox, terminal (whatever) nothing is ever found.

Something went wrong, ideas?

Thank you in advance - yet again!

-Christian.

---

### Post by Krytarik on 2012-01-18
Make sure the packages "unity" and "unity-lens-applications" are installed; the latter of which is a "recommended" package of "unity", and, if missing, will be pulled in automatically when you run:
```
sudo apt-get install --reinstall unity
```Hope that helps.

---

### Post by creiss on 2012-01-19
Mhh,

Thanks for replying but -
no that wasn't it. I tried that. I also tried adding a new user and it worked with that one. So it must be a user setting. 

Uhhh....

---

### Post by Krytarik on 2012-01-19
> **creiss said:**
> I also tried adding a new user and it worked with that one. So it must be a user setting.
Then try deleting the Zeitgeist database:
```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```

---

### Post by creiss on 2012-01-19
Thanks for your reply, did that, still no joy.

Here is the debug:

```

[DEBUG - zeitgeist.fts] Search '(ter*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.133037567139ms
[DEBUG - zeitgeist.fts] Search '(term*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.141143798828ms
[DEBUG - zeitgeist.fts] Search '(termin*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.125885009766ms
[DEBUG - zeitgeist.fts] Search '(terminal*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.124931335449ms
[DEBUG - zeitgeist.fts] Search '(termina*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.14591217041ms

```

---

### Post by creiss on 2012-01-20
If i searchf for terminal this is the complete debug output:

```

creiss@eulie ~ > zeitgeist-daemon -r --log-level=DEBUG
[DEBUG - singleton] Checking for another running instance...
[INFO - zeitgeist.sql] Using database: /home/creiss/.local/share/zeitgeist/activity.sqlite
[DEBUG - zeitgeist.sql] Core schema is good. DB loaded in 1.39188766479ms
[DEBUG - zeitgeist.extension] Searching for system extensions in: /usr/share/zeitgeist/_zeitgeist/engine/extensions
[DEBUG - zeitgeist.extension] Searching for user extensions in: /home/creiss/.local/share/zeitgeist/extensions
[DEBUG - zeitgeist.extension] No extra extensions
[DEBUG - zeitgeist.extension] Found extensions: [<class '_zeitgeist.engine.extensions.datasource_registry.DataSourceRegistry'>, <class '_zeitgeist.engine.extensions.blacklist.Blacklist'>, <class '_zeitgeist.engine.extensions.fts.SearchEngineExtension'>, <class '_zeitgeist.engine.extensions.storagemonitor.StorageMonitor'>]
[DEBUG - zeitgeist.extension] Loading extension 'DataSourceRegistry'
[DEBUG - zeitgeist.datasource_registry] Loaded data-source data from /home/creiss/.local/share/zeitgeist/datasources.pickle
[DEBUG - zeitgeist.extension] Loading extension 'Blacklist'
[DEBUG - zeitgeist.blacklist] No existing blacklist config found
[DEBUG - zeitgeist.extension] Loading extension 'SearchEngineExtension'
[DEBUG - zeitgeist.fts] Opening full text index: /home/creiss/.local/share/zeitgeist/fts.index
[DEBUG - zeitgeist.extension] Loading extension 'StorageMonitor'
[DEBUG - zeitgeist.storagemonitor] Setting storage medium 0861eb42-7c57-45e0-abd6-ed134dee250d 'root' as available
[DEBUG - zeitgeist.storagemonitor] Creating NetworkManager network monitor
[DEBUG - zeitgeist.storagemonitor] NetworkManager network state: 70
[DEBUG - zeitgeist.storagemonitor] Setting storage medium net 'Internet' as available
[INFO - root] Trying to start the datahub
[DEBUG - root] Running datahub (/usr/bin/zeitgeist-datahub) with PID=25368
[INFO - root] Starting Zeitgeist service...
[DEBUG - zeitgeist.fts] Search '(t*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 296 hits in 2.37488746643ms
[DEBUG - zeitgeist.engine] Found 13 events in 0.003288s
[DEBUG - zeitgeist.engine] Got 13 raw events in 0.000396s
[DEBUG - zeitgeist.engine] Got 13 events in 0.001354s
[DEBUG - zeitgeist.engine]     Where time spent in _get_event_from_row in 0.000336s
[DEBUG - zeitgeist.engine]     Where time spent in _get_subject_from_row in 0.000235s
[DEBUG - zeitgeist.engine]     Where time spent in apply_get_hooks in 0.000057s
[DEBUG - zeitgeist.fts] Search '(ter*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 1.21188163757ms

```

---

### Post by ale_vx on 2012-01-20
Do this:


<ctrl> + L  to open terminal
Execute: unity --reset

---

### Post by Krytarik on 2012-01-20
> **creiss said:**
> ```

[DEBUG - zeitgeist.fts] Search '(ter*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.133037567139ms
[DEBUG - zeitgeist.fts] Search '(term*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.141143798828ms
[DEBUG - zeitgeist.fts] Search '(termin*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.125885009766ms
[DEBUG - zeitgeist.fts] Search '(terminal*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.124931335449ms
[DEBUG - zeitgeist.fts] Search '(termina*) AND ((zgem:http://www.zeitgeist-project.com/ontologies/2010/01/27/zg#UserActivity) AND (zgsu:file_*))' gave 0 hits in 0.14591217041ms

```
I've tested that yesterday, and this output doesn't indicate an error with Zeitgeist: when you enter a search term in the Dash, it also searches the user activity, like opened files, for example; and this output simply indicates that there weren't any matching items in that area, it says nothing about apps being searched for, not even when successful.

As I said previously, the package "unity-lens-applications" must be installed; is that the case!? Notice that when you've just installed it, you must restart Unity to make it affect it, easiest done per relogin. Also, when you've checked that both, is the Applications Lens present at the bottom of the Dash?

---

### Post by BC59 on 2012-01-20
> **ale_vx said:**
> Do this:


<ctrl> + L  to open terminal
Execute: unity --reset

CTRL+L doesn't open a terminal. The combination is CTRL+ALT+T.
The command unity --reset is correct but it is superseded by the Unity reinstall, proposed by @Krytarik

---

### Post by Krytarik on 2012-01-20
> **BC59 said:**
> The command unity --reset is correct but it is superseded by the Unity reinstall, proposed by @Krytarik
Well, a reinstall of Unity, or of any other package, for that matter, doesn't change the user's settings, stored in its home directory. But yeah, I don't expect that "unity --reset" would help in this case either.

---

### Post by creiss on 2012-01-22
Hey all!

Thanks for your support this far.
I have tried the --reset flag, the screen flickers a little - with no effect. Even after relog (or reboot) - still can't find any programs, it does find Documents & Stuff tho.

Like I said I doubt reinstalling would fix the issue, as a newly created user (or the guest user) can find programs pretty fast.

I need Ubuntu for Work, and launching everything through an open terminal is not really user friendly. I desperatly need the find programs "feature".

Must be a user setting. Is it possible to deactivate the search for programs? Maybe I hit some key-combination somewhere? Disabled a needed user-daemon? Startup application?

I am out of my wits here...

---

### Post by Krytarik on 2012-01-22
> **creiss said:**
> a newly created user (or the guest user) can find programs pretty fast.
Ok, this (indirectly) answers my first question, if "unity-lens-applications" is installed, and also rules out any general, system-wide issue. (I just noticed that you've mentioned that before already.)

But you didn't answer my second question: is the Applications Lens present in your (own) Dash? Is its underlying daemon running?:
```
ps ax |grep unity-applications-daemon
```If not, do you get any related error messages when you run it manually?:
```
/usr/lib/unity-lens-applications/unity-applications-daemon
```

---

### Post by creiss on 2012-01-23
Hey there,

Thanks for your continuous effort to help me, so much appreciated.
The daemon was **not** running under my username. Launching it directly resulted in no output, but still was unable to find any programs, even after some waiting.

I also tried restarting zeitgeist after starting the applications-daemon, still nogo.

I think we/you are on the right track here :)

-Chris.

---

### Post by creiss on 2012-01-23
One thing i just noticed: If i open the Dashboard and click on "More Apps", "Media Apps" or "Internet Apps" I do get a blank page.

---

### Post by Steeperton on 2012-01-23
I get this occasionally, and I've no idea what's causing it. 

What seems to work is to not start any applications, etc. after booting, and waiting for about a minute after your desktop appears before doing anything. The application lens seems to work fine then. 

Hopefully someone more knowledgeable than I can work out why!

---

### Post by Krytarik on 2012-01-23
> **creiss said:**
> The daemon was **not** running under my username. Launching it directly resulted in no output, but still was unable to find any programs, even after some waiting.
Try restarting Unity after that:
```
unity --replace
```
Btw., you still didn't answer if the Applications Lens is present in your Dash. :D

---

### Post by creiss on 2012-01-23
I just found out one more shred of clue:

When I am logged in I am missing the application icon in the bottom. Like the house (home), the Pen & Pencil (Application), the Document (Documents) and the Note (Music). I am missing the very pen & pencil icon. I guess thats why I cant find any programs.

Now, how do i retrain the dashboard to use the Application "plugin" again?

-Christian.

---

### Post by creiss on 2012-01-24
**SOLVED**

After setting up a VM of my notebook so I could easily revert all changes and after an hour of deleting every single file in my home folder I while continuously restarting the machine I have found the culprit:

```
~/.cache/software-center
```

After deleting this directory and relogging everything worked - even the software center. As to **why** this caused the problem I can only guess.

Thanks for all your help - may this solution help someone else.

-Christian

---

### Post by Krytarik on 2012-01-24
> **creiss said:**
> As to **why** this caused the problem I can only guess.
Yeah, that didn't seem too obvious to me either, in the first moment, but thinking about it, the Applications Lens also shows the "Apps Available for Download", and now it's started to make more sense, good to know! This is yet another reason why those 'feature' shouldn't be enabled in the first place. :P

(Btw., it's planned to provide the user an option to disable that, starting with Ubuntu's next version, Precise 12.04; even though, as of now, the freed up space wouldn't be used by the "Installed" apps instead.)

---

