---
title: "Fork XQF?"
date: 2009-02-24
forum: Gaming &amp; Leisure
---

### Post by Xyhthyx on 2009-02-24
Hi fellow Linux gamers. I am Xyhthyx, the author of Parcellite. I know many of you enjoy gaming in Linux and have come across the excelent XQF tool. I have noticed that it hasn't been updated in a while and neither has qstat and I have started to wonder that the GUI for XQF looks, well.. not good.

And so, before I decide to ruin the XQF program with my version of it, I'm asking the community, would you like me to fork it and design an updated, GNOME-ish, multi-game server browser?

Seeing as the newer games come with their own in-game server browser, XQF serves its purpose really well for the older titles. But let's face it, a lot of us prefer launching a game of ET and Q3 from XQF.

---

### Post by detrate on 2009-03-01
I think this would be a very good idea :).

---

### Post by J.K.Makowka on 2009-03-01
Have you tried contacting the original XQF authors first?

---

### Post by Vadi on 2009-03-01
Agreed, and I'd be willing to help out on the HIG-compliant interface design.

There's no real point in contacting the devs here though - as the program is abandoned, not under active development. It's more like a continuation.

---

### Post by detrate on 2009-03-02
There has already been an update of the Nexuiz protocol for the upcoming 2.5 version.

patch below by divVerent:

```
diff -u qstat-2.11.orig/qstat-2.11/qstat.c qstat-2.11/qstat.c
--- qstat-2.11.orig/qstat-2.11/qstat.c	2006-10-28 14:37:18.000000000 +0200
+++ qstat-2.11/qstat.c	2009-01-08 07:59:23.000000000 +0100
@@ -5990,6 +5990,7 @@
 deal_with_q2_packet( struct qserver *server, char *rawpkt, int pktlen,
 	int check_duplicate_rules)
 {
+    char fragstring[256];
     char *key, *value, *end;
     struct player *player= NULL;
     struct player **last_player= & server->players;
@@ -6073,7 +6074,21 @@
 			server->next_rule = NO_SERVER_RULES;
 		    break;
 		}
-	    rc= sscanf( pkt, "%d %n", &frags, &len);
+	    len = 0;
+	    rc= sscanf( pkt, "%255s %n", &fragstring, &len);
+	    if(rc == 1)
+	    {
+	    	if(isdigit(fragstring[0]) || fragstring[0] == '-')
+		{
+		    frags = atoi(fragstring);
+		    // DarkPlaces allows QC mods to sepcify their own frags
+		    // string, and it should start with an integer representing
+		    // the score.
+		    // This is why this isn't done with sscanf.
+		}
+		else
+		    rc = 0; // this doesn't even START with a number...
+	    }
 	    if ( rc == 1 && pkt[len] != '"')  {
 		pkt+= len;
 		rc= sscanf( pkt, "%d %n", &ping, &len);

```

---

### Post by Kingsley on 2009-03-04
Go for it, dude. XQF could use a facelift.

---

### Post by xeros on 2010-10-14
Did you make any changes, yet?
For example to support Xonotic servers and client?

---

