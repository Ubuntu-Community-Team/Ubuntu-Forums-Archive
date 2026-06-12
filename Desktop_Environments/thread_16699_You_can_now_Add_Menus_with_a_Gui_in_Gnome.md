---
title: "You can now Add Menus with a Gui in Gnome"
date: 2005-02-23
forum: Desktop Environments
---

### Post by delltony on 2005-02-23
I hope this is the correct place to post this but here goes.
I made a program in [php-gtk](http://gtk.php.net/download.php) that will allow you to add menus to gnome in hoary easily.  The code can be edited to suit your needs but this is the basic format. Hope it serves useful to you.

[IMG]http://www.imageark.net/img.php?id=94805[/IMG]

```

<?php
    /* 
    Simple Menu maker for Gnome 2.10
    Author: Tony Stegall
    Email tonyonlinux@gmail.com
    Version 1.2
    Notes:
      Things you must do to run this program
      1) Install php-gtk 
      2) Install php4-dev
      3) Compile php-gtk 
      4) chmod 770 /usr/share/applications
      5) A file by the name of WHATS ENTERED IN THE LAUNCHER NAME.desktop will be made
         so hopefully the names will not conflict be careful on this use something you
         know is not being used by anotherh app cause it will overwrite its desktop file
    To run:
        place this file in any folder where you know its path (ex. /home/tony/phpfiles)
        run by doing the following php --q /home/tony/phpfiles/addmenu.php
     
    Take note:
         more categories can be added as need this is just a generic layout
         you can find the cats under /etc/xdg/menus/application.menu 
         Note the <Category> tag
    */
    if (!class_exists('gtk')){
    	strtoupper(substr(PHP_OS,0,3) == 'WIN')?dl('php_gtk.dll'):dl('php_gtk.so');
    	}
    //Get the initial window with specific s
    //     ettings
    $window = &new GtkWindow();
    $window->set_position(GTK_WIN_POS_CENTER);
    $window->set_title("Add Menu Item to Gnome By Tony Stegall");
    $window->set_border_width(5);
    
    $window->set_default_size(300,300);
    $window->connect_object("destroy", array("gtk","main_quit"));
    $window->set_policy(false, false, false);
    $window->realize();
    
    //Get GTK TABLE and add it to the window
    //     
    $table = &new GtkTable(10,12,false);
    $table->set_row_spacings(5);
    $table->set_col_spacings(5);
    $window->add($table);
// Launcher    
    $name = &new GtkLabel("Launcher Name");
    $name->set_justify(GTK_JUSTIFY_FILL);
    $table->attach($name,0,4,0,1);
    
    $nametext = &new GtkEntry();
    $nametext->set_editable(true);
    //$nametext->set_usize(20,100);
    $table->attach($nametext,5,9,0,1);

// Comment        
    $comment = &new GtkLabel("Comment"); 
    $comment->set_justify(GTK_JUSTIFY_FILL); 
    //$comment->set_usize(20,100);
    $table->attach($comment,0,4,2,3); //0,1,1,2
    
    $commenttext = &new GtkEntry(); 
    $commenttext->set_editable(true); 
    //$commenttext->set_usize(20,100);
    $table->attach($commenttext,5,9,2,3);//2,3,1,2 
    
// Icon Path    
    $icon = &new GtkLabel("Icon Path"); 
    $icon->set_justify(GTK_JUSTIFY_FILL);
    $table->attach($icon,0,4,4,5);
    
    $icontext = &new GtkEntry(); 
    $icontext->set_editable(true); 
    $table->attach($icontext,5,8,4,5);//2,3,1,2 
    $iconbrowse = &new GtkButton("browse");
    $iconbrowse->connect_object('clicked','create_file_selection','icon');
    //$iconbrowse->connect_object('clicked', 'file_selection_ok', $windowFS, 'icon');
    $table->attach($iconbrowse,8,9,4,5);//2,3,6,7
    

//Execution Path
       
    
    $exec = &new GtkLabel("Execution Path"); 
    $exec->set_justify(GTK_JUSTIFY_FILL);
    $table->attach($exec,0,4,6,7);
    
    $exectext = &new GtkEntry(); 
    $exectext->set_editable(true); 
    $table->attach($exectext,5,8,6,7);//2,3,1,2 
    $execbrowse = &new GtkButton("browse");
    $execbrowse->connect_object('clicked','create_file_selection','exec');
    $table->attach($execbrowse,8,9,6,7);//2,3,6,7
    
    
          
    //stuff for dropdown
    $strings = array("AudioVideo", "Education", "Game", "Graphics", "Network", "Office", "Sound", "System", "Utility");
    $catbox = &new GtkVBox(false, 10);
    $catbox->set_border_width(10);
    //$table->add($catbox);
    $table->attach($catbox,5,9,8,9); 
    $cb = &new GtkCombo();
    $cb->set_popdown_strings($strings);
    $cb_entry = $cb->entry;
    $entry = $cb->entry;
    $cb_entry->set_text('Select Category');
    $cb_entry->select_region(0, -1);
    $catbox->pack_start($cb);
    
    $entry->connect('changed', 'printcat');
    

    $submit = &new GtkButton("Submit");
    $submit->connect('clicked','Showdetails');
    $table->attach($submit,7,9,10,11);//2,3,6,7
    
    //function for finding icon
     function file_selection_ok($file_selection,$button) {//button
        global $windows,$exectext,$icontext;
           //print "$buttontype";
	if ($button == 'exec') {
            //print "exec works";
            $tempfile= $file_selection->get_filename();
	    $exectext->set_text($tempfile);//thefile
            //print "$exectext";
	}elseif ($button == 'icon'){//button
            //print "icon works";
            $tempfile = $file_selection->get_filename();
	    $icontext->set_text($tempfile);//thefile
            //print "$icontext";
	}
        
	$windows['file_selection']->hide();
      }
     function create_file_selection($buttontype)
	{
	global $windows;

	//if (!isset($windows['file_selection'])) {
		$windowFS = &new GtkFileSelection('File selection dialog');
		$windows['file_selection'] = $windowFS;
		$windowFS->hide_fileop_buttons();
		$windowFS->set_position(GTK_WIN_POS_MOUSE);
		$windowFS->connect('delete_event', 'delete_event');

		$button_ok = $windowFS->ok_button;
		$button_ok->connect_object('clicked', 'file_selection_ok', $windowFS, $buttontype);
		
		$button_cancel = $windowFS->cancel_button;
		$button_cancel->connect('clicked', 'close_window');

		$action_area = $windowFS->action_area;

		$button = &new GtkButton('Hide Fileops');
		$button->show();
		$button->connect_object('clicked', create_function('$w', '$w->hide_fileop_buttons();'), $windowFS);
		$action_area->pack_start($button, false, false, 0);

		$button = &new GtkButton('Show Fileops');
		$button->show();
		$button->connect_object('clicked', create_function('$w', '$w->show_fileop_buttons();'), $windowFS);
		$action_area->pack_start($button, false, false, 0);
	//}
	if ($windows['file_selection']->flags() & GTK_VISIBLE)
		$windows['file_selection']->hide();
	else
		$windows['file_selection']->show();
	}
    
     function close_window($widget)
	{
	$window = $widget->get_toplevel();
	$window->hide();
	}
		
    function printcat($entry) {
         $entered = $entry->get_text();
         global $varcat;
         $varcat = $entered;
         print $entered."\n";
     }
    function Showdetails(){
    global $window,$commenttext,$icontext,$nametext,$varcat,$exectext; 
    $enteredname = $nametext->get_text();
    $enteredicon = $icontext->get_text();
    $enteredexec = $exectext->get_text();
    $len = strlen($commenttext->get_text()); 
    $newcommenttext = $commenttext->get_chars(0,$len); 
    print "\n Here is what has been wrote to the $enteredname .desktop file => \n 
    		 
                  
                 [Desktop Entry]\n
                 Encoding=UTF-8\n
                 Name=$enteredname\n
                 Comment=$newcommenttext\n
                 Exec=$enteredexec\n
                 Icon=$enteredicon\n
                 Terminal=false\n
                 Type=Application\n
                 Categories=Application;$varcat;";
       //code added to write to file
          $filename = "/usr/share/applications/".$enteredname.'.desktop';
         
       // print "$data is whats in data";
        $fp = fopen( $filename, "w") or die ("Couldn't open $filename");
        
          $data = "
		[Desktop Entry]
                 Encoding=UTF-8
                 Name=$enteredname
		Comment=$newcommenttext
		Exec=$enteredexec
		Icon=$enteredicon
		Terminal=false
		Type=Application
		Categories=Application;$varcat;";
	        

        fwrite( $fp, $data);
        fclose ($fp); 

    Gtk::main_quit();
    }
    $window->show_all();
    gtk::main();
    ?>

```

---

### Post by Darrena on 2005-02-23
Wootage!  Thank You!

---

### Post by rosslaird on 2005-02-23
This is probably the most sought-after gnome feature in Hoary. Thanks very much for putting together a method for accomplishing it.

Now, for those of us who are not uber-geeks, what precisely do we do with this code to get the thing working? (apologies for ignorance)

---

### Post by bored2k on 2005-02-23
[QUOTE=rosslaird]This is probably the most sought-after gnome feature in Hoary. Thanks very much for putting together a method for accomplishing it.

Now, for those of us who are not uber-geeks, what precisely do we do with this code to get the thing working? (apologies for ignorance)[/QUOTE]


Exactly. .. should we gcc the file or what ?

---

### Post by delltony on 2005-02-23
[QUOTE=bored2k]Exactly. .. should we gcc the file or what ?[/QUOTE]
 OK, notice i posted the link for php-gtk.  Go to that site and download the binary source. 
Once you download it you need to run I believe the file is ./buildconfig    you will see it after you untar the file.  The compiling will more than likely fail the first go cause you also need to synaptic and get php4-dev  this will included all the tools needed to develop the php.  Not certain if its needed but also install php-cli (command line).  That should get the configure complete. Once the configuration is done then type make. if that is successful then type make install. Then it will install the program. Then make a php file using gedit and paste the code i wrote in there. Save it and then type php --q /pathtofileyoumade/nameoffile.php 
then the gui should come up and you can go from there. Your first task with the gui should simple be make a launcher for this program. Just in the name type something like Add Menu then comment type Adds a menu item to gnome then select the icon you want to use they are in /usr/share/pixelmaps  then select the exec  once its selected if its this php make sure you go back to the edit box and put php --q infront of it.  then select a category you want to put it in this application would be under system.  then hit submit then go to applications and  notice your cute little icon added.  HOpe this helps.

---

### Post by rosslaird on 2005-02-23
Thanks very much for the guide. It helps a lot.
For the non-programmers among us, this is what I have done so far, and I think I'm almost there:

1. sudo apt-get install php4 php4-dev libglade0-dev libgtk1.2-dev glade
2. Downloaded the sources from [here](http://gtk.php.net/download.php) and extracted them using nautilus (alt-click "Extract here").
2. Navigated in a console to the downloaded source directory.
Typed:

./buildconf
./configure
make
sudo make install

Worked like a charm.

(Note:
You may have to chmod /usr/share/applications to 777:
sudo chmod 777 /usr/share/applications)

Then I just followed the rest of the instructions above.


Ross

---

### Post by rosslaird on 2005-02-23
OK, almost there. I made the php file, ran it, and I get this:

Parse error: parse error, unexpected T_STRING, expecting T_VARIABLE or '{' or '$' in /home/ross/menu_editor.php on line 184
ross@ross:~$ php --q /home/ross/menu_editor.php

Parse error: parse error, unexpected T_STRING, expecting T_VARIABLE or '{' or '$' in /home/ross/menu_editor.php on line 184

Any ideas?

---

### Post by delltony on 2005-02-23
[QUOTE=rosslaird]OK, almost there. I made the php file, ran it, and I get this:

Parse error: parse error, unexpected T_STRING, expecting T_VARIABLE or '{' or '$' in /home/ross/menu_editor.php on line 184
ross@ross:~$ php --q /home/ross/menu_editor.php

Parse error: parse error, unexpected T_STRING, expecting T_VARIABLE or '{' or '$' in /home/ross/menu_editor.php on line 184

Any ideas?[/QUOTE]
 what did you enter for the name it sounds like you entered a number instead of a text variable
try this
Type Add Menu for the launcher name then type a comment like Add menu for Gnome
then  select  icon, then for the exec path type php --q /home/ross/menu_editor.php and hit submit and tell me the results.


Awww: i see what the issue is look down at line 184 it has in there $ exectext it should be $exectext   somehow the copy and paste didn't work correctly.

this should fix the issue right up!

---

### Post by vrecan on 2005-02-23
Nice, Thank you!  Too bad they dont have a php-gtk2+ then it would fit in perfectly.

---

### Post by rosslaird on 2005-02-23
> Awww: i see what the issue is look down at line 184 it has in there $ exectext it should be $exectext somehow the copy and paste didn't work correctly. 

Yup. I edited the spaces out and it worked. That's really a bizarre thing, for the copy and paste to select just this one small item to improperly copy.

Thanks for all the help.

The only glitch I have found in the instructions is that I had to set /usr/share/applications to 777 instead of 770 to get it to work. That's probably some horrible security issue, but I'm the only person on my system.

---

### Post by cka on 2005-02-23
I'm not so much amazed at a GUI menu editor as I am that there's an *actual use* for PHP-GTK now.   :razz:

Great stuff, I'll have to jimmy up some apps myself with this...

---

### Post by bored2k on 2005-02-24
why the need if one can run
nautilus applications:///
File > Create Launcher and do the same ?


btw im sorry im not [-X  playa hatin is just that i find this way sort of clearer

---

### Post by ember on 2005-02-24
[QUOTE=bored2k]why the need if one can run
nautilus applications:///
File > Create Launcher and do the same ?
[/QUOTE]

You can't do that in hoary, that's all ;)

---

### Post by bored2k on 2005-02-24
[QUOTE=ember]You can't do that in hoary, that's all ;)[/QUOTE]

lol thnx 4 clearing that out 4 me, i didnt hav good xperience when warty was beta, so im not using hoary for now  :???:

---

### Post by polymorphic on 2005-03-07
Hi. I love Ubuntu and Gnome, but I was surprised that the ability to configure the menus has gone away. Surely this must be an oversight, and I hope it is going to be fixed properly. I appreciate someone has taken the time to write a PHP script as a workaround, but this has got to be fixed!!

Does anyone know if this is planned to be fixed? Gnome and/or Ubuntu will surely get flack (to be honest, rightfully so) for not providing this facility.

---

### Post by Marble2 on 2005-03-12
I'm getting this error.

greg@Greg:~ $ php --q /home/greg/edit.php

Parse error: parse error, unexpected ')' in /home/greg/edit.php on line 83

---

### Post by dolson on 2005-03-13
Why was this removed anyhow? That's dumb. Why can't we just drag and drop, or right-click, whatever, and have an option? I think that would be very usable, don't you think?

I'd also like to see an option for "Open Location" in the Places menu, but maybe that's just me.

---

### Post by RastaMahata on 2005-03-13
[QUOTE=dolson]Why was this removed anyhow? That's dumb. Why can't we just drag and drop, or right-click, whatever, and have an option? I think that would be very usable, don't you think?

I'd also like to see an option for "Open Location" in the Places menu, but maybe that's just me.[/QUOTE]
 waaait a second there... gnome 2.10 doesnt have right click > create launcher?

And I agree, dragging is ++ for me :D

---

### Post by Iczelyceton on 2005-05-16
[QUOTE=rosslaird]Thanks very much for the guide. It helps a lot.
For the non-programmers among us, this is what I have done so far, and I think I'm almost there:

1. sudo apt-get install php4 php4-dev libglade0-dev libgtk1.2-dev glade
2. Downloaded the sources from [here](http://gtk.php.net/download.php) and extracted them using nautilus (alt-click "Extract here").
2. Navigated in a console to the downloaded source directory.
Typed:

./buildconf
./configure
make
sudo make install

Worked like a charm.

(Note:
You may have to chmod /usr/share/applications to 777:
sudo chmod 777 /usr/share/applications)

Then I just followed the rest of the instructions above.


Ross[/QUOTE]

Hi Ross,

in your first described step you also need to get php4-cli, gcc and g++. Otherwise ./configure will fail.

Iczelyceton

---

### Post by Iczelyceton on 2005-05-16
> **delltony]I hope this is the correct place to post this but here goes.
I made a program in [php-gtk](http://gtk.php.net/download.php) that will allow you to add menus to gnome in hoary easily.  The code can be edited to suit your needs but this is the basic format. Hope it serves useful to you.

[IMG]http://www.imageark.net/img.php?id=94805[/IMG]

```

<?php
    /* 
    Simple Menu maker for Gnome 2.10
    Author: Tony Stegall
    Email tonyonlinux@gmail.com
    Version 1.2
    Notes:
      Things you must do to run this program
      1) Install php-gtk 
      2) Install php4-dev
      3) Compile php-gtk 
      4) chmod 770 /usr/share/applications
      5) A file by the name of WHATS ENTERED IN THE LAUNCHER NAME.desktop will be made
         so hopefully the names will not conflict be careful on this use something you
         know is not being used by anotherh app cause it will overwrite its desktop file
    To run:
        place this file in any folder where you know its path (ex. /home/tony/phpfiles)
        run by doing the following php --q /home/tony/phpfiles/addmenu.php
     
    Take note:
         more categories can be added as need this is just a generic layout
         you can find the cats under /etc/xdg/menus/application.menu 
         Note the <Category> tag
    */
    if (!class_exists('gtk')){
    	strtoupper(substr(PHP_OS,0,3) == 'WIN')?dl('php_gtk.dll'):dl('php_gtk.so') said:**
> ->hide();
      }
     function create_file_selection($buttontype)
	{
	global $windows;

	//if (!isset($windows['file_selection'])) {
		$windowFS = &new GtkFileSelection('File selection dialog');
		$windows['file_selection'] = $windowFS;
		$windowFS->hide_fileop_buttons();
		$windowFS->set_position(GTK_WIN_POS_MOUSE);
		$windowFS->connect('delete_event', 'delete_event');

		$button_ok = $windowFS->ok_button;
		$button_ok->connect_object('clicked', 'file_selection_ok', $windowFS, $buttontype);
		
		$button_cancel = $windowFS->cancel_button;
		$button_cancel->connect('clicked', 'close_window');

		$action_area = $windowFS->action_area;

		$button = &new GtkButton('Hide Fileops');
		$button->show();
		$button->connect_object('clicked', create_function('$w', '$w->hide_fileop_buttons();'), $windowFS);
		$action_area->pack_start($button, false, false, 0);

		$button = &new GtkButton('Show Fileops');
		$button->show();
		$button->connect_object('clicked', create_function('$w', '$w->show_fileop_buttons();'), $windowFS);
		$action_area->pack_start($button, false, false, 0);
	//}
	if ($windows['file_selection']->flags() & GTK_VISIBLE)
		$windows['file_selection']->hide();
	else
		$windows['file_selection']->show();
	}
    
     function close_window($widget)
	{
	$window = $widget->get_toplevel();
	$window->hide();
	}
		
    function printcat($entry) {
         $entered = $entry->get_text();
         global $varcat;
         $varcat = $entered;
         print $entered."\n";
     }
    function Showdetails(){
    global $window,$commenttext,$icontext,$nametext,$varcat,$exectext; 
    $enteredname = $nametext->get_text();
    $enteredicon = $icontext->get_text();
    $enteredexec = $exectext->get_text();
    $len = strlen($commenttext->get_text()); 
    $newcommenttext = $commenttext->get_chars(0,$len); 
    print "\n Here is what has been wrote to the $enteredname .desktop file => \n 
    		 
                  
                 [Desktop Entry]\n
                 Encoding=UTF-8\n
                 Name=$enteredname\n
                 Comment=$newcommenttext\n
                 Exec=$enteredexec\n
                 Icon=$enteredicon\n
                 Terminal=false\n
                 Type=Application\n
                 Categories=Application;$varcat;";
       //code added to write to file
          $filename = "/usr/share/applications/".$enteredname.'.desktop';
         
       // print "$data is whats in data";
        $fp = fopen( $filename, "w") or die ("Couldn't open $filename");
        
          $data = "
		[Desktop Entry]
                 Encoding=UTF-8
                 Name=$enteredname
		Comment=$newcommenttext
		Exec=$enteredexec
		Icon=$enteredicon
		Terminal=false
		Type=Application
		Categories=Application;$varcat;";
	        

        fwrite( $fp, $data);
        fclose ($fp); 

    Gtk::main_quit();
    }
    $window->show_all();
    gtk::main();
    ?>

```
 This is good for adding new entries in the menu. But how do I delete entries?

Iczelyceton

---

