---
title: "Can you sort the &quot;New Document&quot; menu MANUALLY (custom sorting) in Nautilus?"
date: 2015-11-16
forum: Desktop Environments
---

### Post by GhettoGirl on 2015-11-16
As the title says, I'm looking for a way to manually sort the **entries** in the *"New Document"* context-menu of Nautilus (v3.14.2). The reason why I'm trying to do this, is to find my templates quicker and easier. Alphabetically sorting is to primitive for me. :biggrin:
A awesome feature would also be the possibility to add separator lines to the menu to find templates even quicker. Oh, and *Icon Support* for folders, there are currently no icons displaying for folders (nested *"New Document"* menu).

I tried to manipulate the **timestamp** of my templaes using [COLOR=#800080]**touch**[/COLOR] and set the sorting for the templates folder to *"By Modification Date"*, but that didn't worked. ](*,) The menu still sorts everything alphabetically...

Currently I have the following templates: (I would like to have it sorted this way, not alphabetically)

[LIST]
[*]*Office* [-> folder]
[LIST]
[*](some LibreOffice templates) 
[/LIST]
  
[*]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; (a separator would be nice here) 
[*]**Shell Script** (simple shell script template) 
[*]**Steam Game Launcher (Linux)** (complex script to workaround the issue, that steam doesn't have a _quit with game_ option) 
[*]**Steam Game Launcher (Windows)** (same for the windows version using wine) 
[*]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; (a separator would be nice here) 
[*]**Wine Launcher** (simple template which contains stuff like WINEPREFIX, WINEARCH, winecfg, winetricks, etc. - I have 18 WINEPREFIXes currently) 
[*]**PlayOnLinux Wine Launcher** (same as above, but optimized for PlayOnLinux) 
[*][there are most likely more to come, I make extensive use of templates] :D 
[/LIST]

I'm willing to recompile nautilus from source to accomplish my needs, but I don't know what file to modify.
[COLOR=#ff0000]**I have C/C++ experience!**[SIZE=1] (and I know how to use Google - because I have no GTK experience, I'm Qt developer)[/SIZE][/COLOR]

[IMG]http://ibin.co/2MmvxDwdZVmR[/IMG]

[HR][/HR]
Can someone guidance me a bit to accomplish my target? :mrgreen:

Thanks in advance.

---

### Post by mc4man on 2015-11-16
Configurable is  anathema to gnome devs so there won't be any built-in or easy way. You could look thru src/nautilus-view.c & libnautilus-private/nautilus-file-utilities.c to see if anything adjustable.
Otherwise it does sort by number at front of file name before it does alphabetically.
As far as a separator probably not possible even if you find a source edit that works for you, again a number----------------------  would 'serve' as a separator

---

### Post by GhettoGirl on 2015-11-16
Thanks for the reply :D I found the code.

The following function is responsible for the *"New Document"* menu. I need to change the sorting part.

**src/nautilus-view.c**
```
static gboolean
update_directory_in_templates_menu (NautilusView *view,
                    const char *templates_directory_uri,
                    NautilusDirectory *directory)
```

**libnautilus-private/nautilus-file.c**
```
GList *
nautilus_file_list_sort_by_display_name (GList *list)

/* modification added by me */
GList *
nautilus_file_list_sort_by_modification_date (GList *list)
```

I'm working on it now... :)
[SIZE=1]
The part with the separators should be fun to implement.[/SIZE]

---

### Post by GhettoGirl on 2015-11-16
I finished the sorting part :D

[IMG]http://ibin.co/2MoRdoldTjJg[/IMG]
[HR][/HR]
In the file **src/nautilus-view.c**
```
static gboolean
update_directory_in_templates_menu (NautilusView *view,
                    const char *templates_directory_uri,
                    NautilusDirectory *directory)
{
    ...
   //file_list = nautilus_file_list_sort_by_display_name (filtered);
   file_list = nautilus_file_list_sort_by_modification_date (filtered);
    ...
}

```

In the file [B]libnautilus-private/nautilus-file.c
[/B]The library had already built-in functions, so it was easy to implement/change ;)
```
static int
compare_by_modification_date (NautilusFile *file_1, NautilusFile *file_2)
{
        return nautilus_file_compare_for_sort(file_1,
                                              file_2,
                                              NAUTILUS_FILE_SORT_BY_MTIME,
                                              1,
                                              0);

}

static int
compare_by_modification_date_cover (gconstpointer a, gconstpointer b)
{
    return compare_by_modification_date (NAUTILUS_FILE (a), NAUTILUS_FILE (b));
}

/**
 * nautilus_file_list_sort_by_modification_date
 * 
 * Sort the list of files by modification date.
 * @list: GList of files.
 **/
GList *
nautilus_file_list_sort_by_modification_date (GList *list)
{
    return g_list_sort (list, compare_by_modification_date_cover);
}
```

I'm posting this, in case others are interested in changing the default sorting for the *"New Document"* menu.

[SIZE=1]Now the fun with the separators begins...[/SIZE]

---

### Post by mc4man on 2015-11-17
So would this be the gist of what you did (sorts older > newer here) or did you have a specific place to enter new code in libnautilus-private/nautilus-file.c ?
```
--- nautilus-3.14.2.orig/libnautilus-private/nautilus-file.c
+++ nautilus-3.14.2/libnautilus-private/nautilus-file.c
@@ -8133,6 +8133,35 @@ nautilus_file_info_iface_init (NautilusF
 	iface->invalidate_extension_info = nautilus_file_invalidate_extension_info;
 }
 
+static int
+compare_by_modification_date (NautilusFile *file_1, NautilusFile *file_2)
+{
+        return nautilus_file_compare_for_sort(file_1,
+                                              file_2,
+                                              NAUTILUS_FILE_SORT_BY_MTIME,
+                                              1,
+                                              0);
+
+}
+
+static int
+compare_by_modification_date_cover (gconstpointer a, gconstpointer b)
+{
+    return compare_by_modification_date (NAUTILUS_FILE (a), NAUTILUS_FILE (b));
+}
+
+/**
+ * nautilus_file_list_sort_by_modification_date
+ * 
+ * Sort the list of files by modification date.
+ * @list: GList of files.
+ **/
+GList *
+nautilus_file_list_sort_by_modification_date (GList *list)
+{
+    return g_list_sort (list, compare_by_modification_date_cover);
+}
+
 #if !defined (NAUTILUS_OMIT_SELF_CHECK)
 
 void
--- nautilus-3.14.2.orig/src/nautilus-view.c
+++ nautilus-3.14.2/src/nautilus-view.c
@@ -5513,7 +5513,8 @@ update_directory_in_templates_menu (Naut
 	filtered = nautilus_file_list_filter_hidden (file_list, FALSE);
 	nautilus_file_list_free (file_list);
 
-	file_list = nautilus_file_list_sort_by_display_name (filtered);
+	//file_list = nautilus_file_list_sort_by_display_name (filtered);
+	file_list = nautilus_file_list_sort_by_modification_date (filtered);
 
 	num = 0;
 	any_templates = FALSE;
```

---

### Post by GhettoGirl on 2015-11-17
here is the **.patch** file

```
--- nautilus-3.14.2.orig/libnautilus-private/nautilus-file.c
+++ nautilus-3.14.2/libnautilus-private/nautilus-file.c
@@ -67,6 +67,7 @@
 #include <time.h>
 #include <unistd.h>
 #include <sys/stat.h>
+#include <sys/types.h>
 
 #ifdef HAVE_SELINUX
 #include <selinux/selinux.h>
@@ -2930,6 +2931,16 @@ compare_by_display_name (NautilusFile *f
 }
 
 static int
+compare_by_modification_date (NautilusFile *file_1, NautilusFile *file_2)
+{
+        return nautilus_file_compare_for_sort(file_1,
+                                              file_2,
+                                              NAUTILUS_FILE_SORT_BY_MTIME,
+                                              1,
+                                              0);
+}
+
+static int
 compare_by_directory_name (NautilusFile *file_1, NautilusFile *file_2)
 {
     return strcmp (file_1->details->directory_name_collation_key,
@@ -7743,6 +7754,12 @@ compare_by_display_name_cover (gconstpoi
     return compare_by_display_name (NAUTILUS_FILE (a), NAUTILUS_FILE (b));
 }
 
+static int
+compare_by_modification_date_cover (gconstpointer a, gconstpointer b)
+{
+    return compare_by_modification_date (NAUTILUS_FILE (a), NAUTILUS_FILE (b));
+}
+
 /**
  * nautilus_file_list_sort_by_display_name
  * 
@@ -7755,6 +7772,18 @@ nautilus_file_list_sort_by_display_name
     return g_list_sort (list, compare_by_display_name_cover);
 }
 
+/**
+ * nautilus_file_list_sort_by_modification_date
+ * 
+ * Sort the list of files by modification date.
+ * @list: GList of files.
+ **/
+GList *
+nautilus_file_list_sort_by_modification_date (GList *list)
+{
+    return g_list_sort (list, compare_by_modification_date_cover);
+}
+
 static GList *ready_data_list = NULL;
 
 typedef struct 
--- nautilus-3.14.2.orig/src/nautilus-view.c
+++ nautilus-3.14.2/src/nautilus-view.c
@@ -5269,7 +5269,8 @@ update_directory_in_scripts_menu (Nautil
     filtered = nautilus_file_list_filter_hidden (file_list, FALSE);
     nautilus_file_list_free (file_list);
 
-    file_list = nautilus_file_list_sort_by_display_name (filtered);
+    //file_list = nautilus_file_list_sort_by_display_name (filtered);
+        file_list = nautilus_file_list_sort_by_modification_date (filtered);
 
     any_scripts = FALSE;
     for (node = file_list; node != NULL; node = node->next) {
@@ -5485,6 +5486,8 @@ directory_belongs_in_templates_menu (con
     return TRUE;
 }
 
+
+
 static gboolean
 update_directory_in_templates_menu (NautilusView *view,
                     const char *templates_directory_uri,
@@ -5517,7 +5520,8 @@ update_directory_in_templates_menu (Naut
     filtered = nautilus_file_list_filter_hidden (file_list, FALSE);
     nautilus_file_list_free (file_list);
 
-    file_list = nautilus_file_list_sort_by_display_name (filtered);
+    //file_list = nautilus_file_list_sort_by_display_name (filtered);
+        file_list = nautilus_file_list_sort_by_modification_date (filtered);
 
     num = 0;
     any_templates = FALSE;


```

I added my code below the other sorting functions and followed the coding guidelines of nautilus.
I also changed the sorting of the scripts menu, since it was so easy :mrgreen:

But I have no idea how to probably add separators. I had to parse a config file or something to accomplish that :???:
Also I have no idea whats wrong with the sub menu (folders) icons...

---

