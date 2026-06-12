---
title: "Synchronising with Google Calendar"
date: 2007-02-04
forum: Desktop Environments
---

### Post by dlai on 2007-02-04
First of all: I have been looking for this for quite some time... Because I found it annoying that I could not use Google Calendar, when in evolution. By that I mean also edit in the calendar.
I found a way!
And here it is:

First you go to your sources.list or your synaptic and add third party repositories, this is the repository you need to add:

```
deb http://www.in.fh-merseburg.de/~jahn/ edgy main
```

There is also a deb-src repository.

after that you install libopensync0, libopensync-plugin-google-calendar, libopensync-plugin-evolution2 and msynctool

```
sudo apt-get install libopensync0 libopensync-plugin-evolution2 libopensync-plugin-google-calendar msynctool
```

Here comes the tricky part

```
msynctool --addgroup GoogleCalendar
```


```
msynctool --addmember GoogleCalendar google-calendar
```

```
msynctool --addmember GoogleCalendar evo2-sync
```

This should bring forward a configuration in nano, where you can add your username and password

```
msynctool --configure GoogleCalendar 1
```

```
msynctool --sync GoogleCalendar
```

Now it should be syncing, mine went a bit cold for a while.. but just give it some time...

You can also use the multisync-gui which is available in the repository as well...

The Calendar tasks will appear in your default Personal account in your calendars unless you change the location manually by using:


```
msynctool --configure GoogleCalendar 2
```

Good Luck!

I think this program is still in beta, so be aware!

---

### Post by cyber_bushi on 2007-02-04
```
Member 1 of type google-calendar had an error while getting changes: Helper exited abnormally
Member 1 of type google-calendar just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members

```

Did anyone also experience this and are there any logfiles that show more details?

regards,

cb

---

### Post by dlai on 2007-02-04
hmm... sounds strange did not have any such problems

---

### Post by edmondt on 2007-02-05
Is this a two way sync? :KS

---

### Post by dlai on 2007-02-05
Yes it is... it still kind of buggy though...

---

### Post by claypole on 2007-02-05
I've had the same problem as cyber_bushi:

Member 1 of type google-calendar had an error while getting changes: Helper exited abnormally
Member 1 of type google-calendar just disconnected
Member 2 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members

Any news? :confused:

---

