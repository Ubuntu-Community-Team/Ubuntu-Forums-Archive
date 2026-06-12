---
title: "Notes 8.5 dominoactionbar"
date: 2009-01-24
forum: General Help
---

### Post by wohenben on 2009-01-24
When viewing notes 8.5 (beta) apps via firefox on 8.04, the action bar (with Save, Cancel, etc) doesn't always appear.  
Sometimes it appears briefly, then vanishes.  
Sometimes it just never appears.  
Sometimes I can refresh the page and get it to appear.
Sometimes I get the message "Applet DominoActionbar notinited"
Sometimes the message is "Applet DominoActionBar bail"

The point is, it's not repeatable (except that it usually fails one way or another).  Running the same app via firefox on Win XP works fine, so it looks like something to do with firefox/java on Ubuntu.

Any suggestions?  I have searched all the logs I can think of, Notes/Domino & Ubuntu, but nothing so far (but there may be other logs I can check?).

---

### Post by jamesstansell on 2009-01-25
If you are running 32-bit ubuntu then try this.

```

$ sudo aptitude install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun

```

and restart Firefox.

For 64-bit ubuntu there is a sticky thread about java in the 64-bit forum.

---

