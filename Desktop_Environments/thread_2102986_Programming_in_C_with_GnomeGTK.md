---
title: "Programming in C with Gnome/GTK"
date: 2013-01-08
forum: Desktop Environments
---

### Post by Baasha on 2013-01-08
I am not sure this is the right forum for this question, but if not free free to bump me to the right one.

I am running Ubuntu 12.04.  I have been trying to learn how to use graphics in C.  I have the Gnome 3 development files installed on my machine, which include all the GKT3 files.  However, when I try to complile the following code I get a 'no such file or directory' error message referring to the gtk header files.  I am sure I am missing some simple thing but I am not experienced enough to know what it is.  Can someone point me in the right direction?

Thx

```

#include <gtk/gtk.h>
 
int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *label;
 
    gtk_init(&argc, &argv);
 
    /* Create the main, top level window */
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
 
    /* Give it the title */
    gtk_window_set_title(GTK_WINDOW(window), "Hello, world!");
 
    /*
    ** Map the destroy signal of the window to gtk_main_quit;
    ** When the window is about to be destroyed, we get a notification and
    ** stop the main GTK+ loop by returning 0
    */
    g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
 
    /*
    ** Assign the variable "label" to a new GTK label,
    ** with the text "Hello, world!"
    */
    label = gtk_label_new("Hello, world!");
 
    /* Plot the label onto the main window */
    gtk_container_add(GTK_CONTAINER(window), label);
 
    /* Make sure that everything, window and label, are visible */
    gtk_widget_show_all(window);
 
    /*
    ** Start the main loop, and do nothing (block) until
    ** the application is closed
    */
    gtk_main();
 
    return 0;
}

```

---

### Post by steeldriver on 2013-01-08
You might get better advice in the programming subforum... but at the risk of making an idiot of myself how are you compiling? are you using pkg-config to add include / link flags?

```
g++ -c ... `pkg-config --cflags gtk+-3.0` ...
``````
g++ -o ... `pkg-config --libs gtk+-3.0` ... 
```

---

