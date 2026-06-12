---
title: "Sync Evolution between two computers"
date: 2009-03-31
forum: General Help
---

### Post by old_toby on 2009-03-31
Hello

Has someone found a decent solution to sync evolution directly between two computers (eg. my desktop and my netbook) without the use of an external server like scheduleworld or myfunambol? I tried to use Opensync with syncml-http-server on one computer and syncevolution on the other, but it didn't work out at all.

Is there a Howto or something similar?

---

### Post by James_Lochhead on 2009-03-31
How are the two computers connecting? The Internet, a LAN, Bluetooth?

If it is over Bluetooth or a LAN you could just rsync the physical files maybe. No idea about specifics though.

---

### Post by old_toby on 2009-03-31
They're connecting over LAN

The problem with syncing just the files is, when I change something on the netbook and something on the desktop and then sync, one of the changes will be lost.

I dream of syncing it just the way you sync a palm with the desktop.

---

### Post by mimor on 2009-04-12
You can play around with rsync in a cron-job ;)
I never succeeded doing this myself, but didn't put a lot of time in it.

---

### Post by rplantz on 2009-04-17
I figured out a way to do it between my desktop and laptop machines. Here is the way I did it.

Set up both machines:

1. Install multisync, multisync-tools, opensync-plugin-evolution, opensync-plugin-file, and unison. Assumes you have openssh-server and openssh-client.

2. Create a folder, say evo_sync

3. Create a SyncGroup: msynctool --addgroup evolution

4. Add two members:
```

    ~$ msynctool --addmember evolution evo2-sync
    ~$ msynctool --addmember evolution file-sync

```
5. Configure the group.
   a. Configure the first member. The evo2-sync member specifies where your evolution address, calendar, and task files are located. If you are using the default locations, there is nothing to do here. If not, you need to change them. (Uses the joe editor.)
```

    ~$ msynctool --configure evolution 1
      <config>
        <address_path>default</address_path>
        <calendar_path>default</calendar_path>
        <tasks_path>default</tasks_path>
      </config>

```
   b. Configure the second member. The file-sync member specifies the folder where you want the sync files placed. You need to put the path in here. I have added my path name between <path> and </path>.
```

    ~$ msynctool --configure evolution 2
      <?xml version="1.0"?>
      <config>
        <!-- directory path for file-sync -->
        <path>/home/bob/evo_sync</path>

        <!-- should care of subdirectories (TRUE or FALSE) -->
        <recursive>FALSE</recursive>
      </config>

```
6. Look at what you have done.
```

   ~$ msynctool --showgroup evolution
   Groupname: evolution
   Member 1: evo2-sync
	   Configuration : <config>
     <address_path>default</address_path>
     <calendar_path>default</calendar_path>
     <tasks_path>default</tasks_path>
   </config>

   Member 2: file-sync
	   Configuration : <?xml version="1.0"?>
   <config>
     <!-- directory path for file-sync -->
     <path>/home/bob/evo_sync</path>

     <!-- should care of subdirectories (TRUE or FALSE) -->
     <recursive>FALSE</recursive>
   </config>

```


To sync the two machines:

1. On each machine run
```

     ~$ evolution --force-shutdown
     ~$ msynctool --sync evolution

```
2. Use unison to synchronize the two evo2-sync folders. From my desktop machine I do
```

     ~$ unison evo_sync ssh://bob@bob-laptop.local/evo_sync

```
3. On each machine run
```

     ~$ msynctool --sync evolution

```

It's a little work to set everything up, but very easy to use once you have done that. The first time you run it there will be lots of changes. I accepted all the defaults, which usually meant hitting the return key N times.

BTW, I just upgraded both my desktop and laptop to 9.04 RC, and the sync still works. Apparently there are some format changes because there were lots of changes. But everything looks okay on both machines.

As always, please point out any errors that I have made in this.

---

### Post by sau99ms on 2009-07-24
> **old_toby said:**
> Hello

Has someone found a decent solution to sync evolution directly between two computers (eg. my desktop and my netbook) without the use of an external server like scheduleworld or myfunambol? I tried to use Opensync with syncml-http-server on one computer and syncevolution on the other, but it didn't work out at all.

Is there a Howto or something similar?


You could sign up for a google account and then access your google calendar, email and contacts in Evolution across the 2 computers as I'm currently doing.

Weblink for more info: [http://linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps](http://linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps)

Hope this helps,

Mark

---

