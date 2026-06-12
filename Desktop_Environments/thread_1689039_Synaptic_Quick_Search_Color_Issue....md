---
title: "Synaptic Quick Search Color Issue..."
date: 2011-02-16
forum: Desktop Environments
---

### Post by LordDelta on 2011-02-16
So, I'm not sure that anyone else out there has this issue.

In short, this is my problem:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=183606&stc=1&d=1297854615[/IMG]

Basically, I happen to like dark themes. I'm currently using one that I've sort of patched together atm, a mix between Divinorum Green, and Ambiance, and a couple others like Elegant Gnome for icons, and the Dark pointer theme.

Sad to say, it seems most applications have been designed with light themes in mind, and usually this isn't a problem for me; I just stop using the poorly designed app and look for a better one, or a way to turn off the offending functionality. Or, attempt to see if I can fix my theme settings (I already have a customized version of the Divinorum Green, because the menu png was done wrong).

However, for me, the Synaptic Package Manager tends to be a crucial bit of software that I use nearly every day. I used to use the Quick Search box, and still do, however it is currently nigh un-usable, as seen above.

List of things I've tried:
Looking through my gtkrc files in Divinorum Green.
Looking through my metacity files in Ambiance
Looking through the glade files for Synaptic 0.63.1

After that last one, I noticed it isn't actually in the toolbar by "design"...leading me to wonder where it comes from, how it highlights its stuff, and if maybe I can patch the code somewhere, if anyone knows where that is...

It should be noted that the box behaves fine if only one character has been entered, the highlight seems to be per-theme settings, its only when the "search" begins that it seems to change color...leading me to believe that it is a code event, and probably not a gtkrc setting. Like I said, if anyone knows where the code for this box can be found...

---

### Post by jerrrys on 2011-02-16
you should be able to tweak your settings with GCC

[ATTACH]183653[/ATTACH]

---

### Post by JOHNNYG713 on 2011-02-16
Same issue here !  I have learned to live with it ! BUT If an answer can be found that would be GREAT !! :D I have looked in to GCC, with no Love !

---

### Post by jerrrys on 2011-02-16
GCC is a pain at first to understand, but it can do a lot

---

### Post by JOHNNYG713 on 2011-02-16
> **jerrrys said:**
> GCC is a pain at first to understand, but it can do a lot

Yes, I do agree on both points ! Once you get to experimenting with it, you can do just about anything with it ! Except change that dam input window and, The attention window in Appearances that tells you "this theme will not look right because xxxxxx is not installed ! I would really like to see Linux themes become more like Window Blinds that you can customize EVERY aspect of the Metacity and GTK, with out the "under" "Zenity" having it's way ! But thats a rant for another time and another thread !  :p ):P 
Think Zenity transparency ! = Great Themes !!

---

### Post by LordDelta on 2011-02-16
I must agree with this sentiment.

Btw, further research shows why the input box is missing from the source. Using Synaptic ( :P ) to find out that I need a ubuntu specific version of the source that adds the quick search box. It is indeed in the glade files. And I have it built (after figuring out that it needed a command not present on the system). And I just have to figure out how glade files are read by the GtkBuilder, shouldn't be too hard...will report back with more soon!

--UPDATE Seems the variable is _entry_fast_search, defined in rgmainwindow.h, though I haven't figured out where its been set/initialized yet. For reference's sake in case anyone else can do something with this.

--UPDATE 2 Seems like there is a synaptic.conf mentioned in the main c++ file... Anyone know if this perhaps would solve our problem?

---

### Post by LordDelta on 2011-02-16
I found the issue.

...unrelated side note, the way synaptic initializes is...interesting.

Back to the issue.

Like I suspected, somebody hard-coded the value directly into the code:

```
gboolean RGMainWindow::xapianDoSearch(void *data)
{
   RGMainWindow *me = (RGMainWindow *) data;
   const gchar *str = gtk_entry_get_text(GTK_ENTRY(me->_entry_fast_search));

   me->_fastSearchEventID = -1;
   me->setBusyCursor(true);
   RGFlushInterface();
   if(str == NULL || strlen(str) <= 1) {
      // reset the color
      gtk_widget_modify_base(me->_entry_fast_search, GTK_STATE_NORMAL, NULL);
      // if the user has cleared the search, refresh the view
      // Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
      // at us, see LP: #38397 for more information
      gtk_tree_view_set_model(GTK_TREE_VIEW(me->_treeView), NULL);
      me->_lister->reapplyFilter();
      me->refreshTable();
      me->setBusyCursor(false);
   } else if(strlen(str) > 1) {
      // only search when there is more than one char entered, single
      // char searches tend to be very slow
      me->setBusyCursor(true);
      RGFlushInterface();
      gtk_tree_view_set_model(GTK_TREE_VIEW(me->_treeView), NULL);
      me->refreshTable();
      // set color to a light yellow to make it more obvious that a search
      // is performed
     [COLOR="Red"] GdkColor yellowish = {0, 63479,63479,48830};
      gtk_widget_modify_base(me->_entry_fast_search, GTK_STATE_NORMAL, &yellowish);[/COLOR]
   }
   me->setBusyCursor(false);

   return FALSE;
}
```

So, anyone who wants to change their theme, to, say, a dark one, with white on yellow, is kinda screwed.

Solution:

A. Change the value and recompile, replace the packaged synaptic manager (how does that even work...if you mess up synaptic's reference to itself...)

B. Fix it to theme along with everything else.

C. Allow for some config variable.

I'll see if I can get any of these implemented, I might just file a bug and recompile for myself though...

Proof that this was the problem:

[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=183679&stc=1&d=1297917346[/IMG]

After making the following, change, recompiling, and running:

```

      GdkColor yellowish = {0, 63479,0,0};
      gtk_widget_modify_base(me->_entry_fast_search, GTK_STATE_NORMAL, &yellowish);
```

---

### Post by JOHNNYG713 on 2011-02-17
OMG ! You are truly a gift ! :KS this is just the thing that makes us do  what we do !! Fix what the overlords have shrugged !! ( Yea that'll  work....Next) It is this attention to detail that will make Linux top  dog ! Thanks to people like you! Root out the issue and solve it ! I  mean,.... Really !!

GdkColor  **Yellowish **= {0. 63479.63479,48830 XXXXcetra !!! Blah blah blah !
**Yellowish !!???**
 I am no coder but how bout !

 GdkColor = Theme {default} color= theme default window "active background" ?>}=@theme)>
     ) colorize = true = Blahblahbalalala

 Or something ! I love dark themes and we need to get this through there  heads ! If you hard code a zenity theme then you best be Damn sure it  works ! With light and dark themes ! ((As a side note;:  GOD I hope GTK 3.0 is NOT a rehash  of the same "ol" same " o " ! )). Thank you for **this fix** ! I will pass it on to MANY people ! And incorporate it in my new themes as a "how to" ! as well as existing ones ! You do know that this means there will be a lot of "Themers" Updating there stuff with a "how to" ! KUDOS my friend ! on this find ! KUDOS !!:D):P Don't be surprised if this gets picked up by all the Linux sites ! webupd8 and such, this is a great find !
 P.S. Now I can color those pesky box's any color I want ! WOOO HOO !

---

