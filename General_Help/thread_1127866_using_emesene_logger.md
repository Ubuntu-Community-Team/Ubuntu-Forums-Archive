---
title: "using emesene logger"
date: 2009-04-16
forum: General Help
---

### Post by FraggedLocust on 2009-04-16
I'm looking for a query that will return the messages that contain a specific string. Is this possible? It looks like the database doesn't actually store message data in plain text, but then what is the point of the logger? Eg. I'm looking for messages that contain hyperlinks, so I'm looking for %[http://%](http://%)

---

### Post by Agent ME on 2009-04-16
I'm not sure how emesene logs its messages, but if its using some sort of text files, then the command 'grep' is your friend.

Entering
```
grep "search string" *
```
in a terminal will search all files in the current directory for "search string".

I know that the pidgin instant messager has a logs folder, which has more folders sorted by service, account, etc, before the actual log files. To grep through all of the files in all of the subdirectories, you can do the following; you might need to do something similar for emesene:
```
cd .purple/logs/
grep "search string" `find . -type f`
```

(Explanation:
In the first code example, I used *, which is replaced by the names of all the files in the current directory. This doesn't include files in subdirectories (and it also includes folders, which grep doesn't do anything with). In the second code example, I used `find . -type f`. This is replaced by the results of the find command, which here is looking into the current directory, and looking for type f (files). Find searches recursively through subdirectories.)

---

### Post by FraggedLocust on 2009-04-17
it uses an sqlite database, and contains tables for user, conversation_events, etc.

---

### Post by FraggedLocust on 2009-04-17
I modified the one from the wiki, so I get the emails of the people that sent messages containing [http://,](http://,) but I don't know what the other column is or how to interpret it.

---

