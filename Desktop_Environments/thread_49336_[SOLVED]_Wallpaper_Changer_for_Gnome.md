---
title: "[SOLVED] Wallpaper Changer for Gnome"
date: 2005-07-15
forum: Desktop Environments
---

### Post by pt123 on 2005-07-15
I have seen that KDE comes with a built in wallpaper changer.

Is there one for GNOME ? that can change the wallpaper at randomly from a directories of pictures at certain intervals?

I read about a program called Wallpaper Tray
[http://www.gnomefiles.org/app.php?soft_id=906](http://www.gnomefiles.org/app.php?soft_id=906)

Looks promising but the link to the site is dead.
[http://planetearthworm.com](http://planetearthworm.com)

Does anyone have the source tar for it or know another location where it can be found?


More importantly are there wallpaper changers for Gnome?

---

### Post by ubuntp on 2005-07-15
You can probably write a simple script that does this. Set one file as your wallpaper, like /home/you/wallpaper.jpg, now write a script that copies a random picture from a given directory to /home/you/wallpaper.jpg, then put the script in your crontab to make it run once a day, a week or even every 5 minutes :D

I must say that's really one of the advantages of linux, no app needed, just a lightweight script.

---

### Post by arnieboy on 2005-07-16
[QUOTE=pt123]I have seen that KDE comes with a built in wallpaper changer.

Is there one for GNOME ? that can change the wallpaper at randomly from a directories of pictures at certain intervals?

I read about a program called Wallpaper Tray
[http://www.gnomefiles.org/app.php?soft_id=906](http://www.gnomefiles.org/app.php?soft_id=906)

Looks promising but the link to the site is dead.
[http://planetearthworm.com](http://planetearthworm.com)

Does anyone have the source tar for it or know another location where it can be found?


More importantly are there wallpaper changers for Gnome?[/QUOTE]
Try wallpaper zapper: [http://www.gnomefiles.org/app.php?soft_id=999](http://www.gnomefiles.org/app.php?soft_id=999)

---

### Post by arnieboy on 2005-07-16
[QUOTE=ubuntp]You can probably write a simple script that does this. Set one file as your wallpaper, like /home/you/wallpaper.jpg, now write a script that copies a random picture from a given directory to /home/you/wallpaper.jpg, then put the script in your crontab to make it run once a day, a week or even every 5 minutes :D

I must say that's really one of the advantages of linux, no app needed, just a lightweight script.[/QUOTE]
Its good to see that u have nice ideas but what u shd remember is that ordinary computer users are NOT expected to write scripts and include them as cron jobs. if u have a script ready and a complete How-to on how to use it, u shd go ahead and help.. sounding unnecessarily geeky scares away newbies and our intention is to attract and not scare them away.
No offence meant as such.

---

### Post by poptones on 2005-07-16
```

#!/bin/bash
WALLPAPERS="/home/poptones/wallpapers" #change this path for your system
ALIST=( `ls -w1 wallpapers` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat $WALLPAPERS/.last` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

```

Save this in a /home/username/wallpapers/ directory as ".randomwallpaper.sh" and make a panel launcher to it with this in the command:

sh /home/*username*/wallpapers/.randomwallpaper.sh

Mine sits right next to my clock, a single click toggles the wallpaper. You can make it run on a cron task if oyu like or you could just add a "sleep *delay*" line to the end.

---

### Post by pt123 on 2005-07-16
[QUOTE=arnieboy]Try wallpaper zapper: [http://www.gnomefiles.org/app.php?soft_id=999](http://www.gnomefiles.org/app.php?soft_id=999)[/QUOTE]
 I tried to install it didn't work.

There seems to be a bug with Ubuntu
[https://gna.org/bugs/?func=detailitem&item_id=2649](https://gna.org/bugs/?func=detailitem&item_id=2649)

---

### Post by arnieboy on 2005-07-16
[QUOTE=pt123]I tried to install it didn't work.

There seems to be a bug with Ubuntu
[https://gna.org/bugs/?func=detailitem&item_id=2649](https://gna.org/bugs/?func=detailitem&item_id=2649)[/QUOTE]
well sorry to hear it didnt work for u.. personally i had never given it a try cuz i never felt the use of a wallpaper changer or i wudnt have suggested it to u.. u can try out poptones' script.

---

### Post by rwabel on 2005-07-17
wallpaper zapper really don't work. Didn't know what someone has already filled a bug report. thanks :-)
 
wp_tray is great. Has much more functions than a script. Somehow it crashes for me. It did work fine in the beginning but some days ago it crashes permantently :-( 

It's really bad that the site is down. I've already removed the source from my HD. Couldn't you find any website hosting it?
 
 I've written a short [howto]("https://wiki.ubuntu.com/WallpaperTray") for wp_tray.

---

### Post by arnieboy on 2005-07-17
[QUOTE=rwabel]wallpaper zapper really don't work. Didn't know what someone has already filled a bug report. thanks :-)
 
wp_tray is great. Has much more functions than a script. Somehow it crashes for me. It did work fine in the beginning but some days ago it crashes permantently :-( 

It's really bad that the site is down. I've already removed the source from my HD. Couldn't you find any website hosting it?
 
 I've written a short [howto]("https://wiki.ubuntu.com/WallpaperTray") for wp_tray.[/QUOTE]

the following site that hosts some recent debs including wp_tray is [http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/)
but therez a problem.. wp_tray needs some recent libs which havent been backported  yet.. its become a pressing problem of late in ubuntu.. backports lag too far behind most updates.. its getting to the point of becoming frustrating.

---

### Post by rwabel on 2005-07-17
[QUOTE=arnieboy]the following site that hosts some recent debs including wp_tray is [http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/)
but therez a problem.. wp_tray needs some recent libs which havent been backported  yet.. its become a pressing problem of late in ubuntu.. backports lag too far behind most updates.. its getting to the point of becoming frustrating.[/QUOTE]
 well at least he has the source package, but it's the old version! Damn, why did I delete the source archive...sorry

---

### Post by poptones on 2005-07-17
I don't understand something.. why do you need all this just to change the wallpaper? The script right up there does it and you can quickly change it to do whatever you want. No installer needed... or is that the problem?

---

### Post by rwabel on 2005-07-17
[QUOTE=poptones]I don't understand something.. why do you need all this just to change the wallpaper? The script right up there does it and you can quickly change it to do whatever you want. No installer needed... or is that the problem?[/QUOTE]
 the installer isn't the problem... :-)
It's nice to have an applet. You can easily configure the interval, the directories etc. You can just click to get the next background.

It's really bad, that I don't have a version I could show you.

Anyway, such things should be in gnome by default

---

### Post by arnieboy on 2005-07-17
[QUOTE=rwabel]the installer isn't the problem... :-)
It's nice to have an applet. You can easily configure the interval, the directories etc. You can just click to get the next background.

It's really bad, that I don't have a version I could show you.

Anyway, such things should be in gnome by default[/QUOTE]
I agree with that. If i have to use a script, i want it to be a permanent one which i dont have to change everytime. I prefer a GUI if I want to do any changes even though am perfectly comfortable changing a few lines or words by opening a script up in a text editor.

---

### Post by pt123 on 2005-07-17
[QUOTE=poptones]I don't understand something.. why do you need all this just to change the wallpaper? The script right up there does it and you can quickly change it to do whatever you want. No installer needed... or is that the problem?[/QUOTE]
 I would rather a have program/applet to do this than having to run 3 different/scripts to manage wp directories, interval change and changing the wallpaper. This would be great to have it in an applet, or desktop configuration like KDE.

---

### Post by geraldo5002 on 2005-07-23
Hi,

The script didnt work in my hoary until I changed the line ALIST for:

ALIST=( `ls -w1 $WALLPAPERS` )

Before that it keeps giving me division by zero errors...

...and picture filenames cannot contain whitespaces (this one I dont know how to solve....)

But it's a good script.

Thanks.

---

### Post by pt123 on 2005-07-23
Is there a way to get the script to work for sub-directories?

---

### Post by poptones on 2005-07-23
[QUOTE=pt123]Is there a way to get the script to work for sub-directories?[/QUOTE]
 OK, I'll mess with it a bit and repost. So long as *someone* finds value in it I won't feel like I'm wasting my time...

---

### Post by Ken.Lank on 2005-07-25
[QUOTE=poptones]
OK, I'll mess with it a bit and repost. So long as *someone* finds value in it I won't feel like I'm wasting my time...
[/QUOTE]

Nice script poptones!  Can you add some comments to the script to help us 'newbies' figure out exactly what is going on (so that I can learn & hopefully start writing my own scripts)?

Thanks,
Ken

---

### Post by geraldo5002 on 2005-07-25
I changed the script a bit, putting a "find" instead of "ls" to generate the ALIST.

But spaces in filenames are a problem... :-(

So i did a little app using mono to change the wallpaper. It's a small console app, but works. I'm gonna create now a small GUI to set the base dir options. Is working fine in my system...

Then I'll try to find some place to put the file for those who want to try it...

---

### Post by rwabel on 2005-07-25
wp tray is back!!!
But I'm stil eager to see any other dev of wp changer!

I don't know why, but I can no longer 'make' wp_tray. On the homepage he states that there are problems with schemas. That's exactly my problem. I hope it gets resolved soon

---

### Post by pt123 on 2005-07-25
[QUOTE=rwabel]wp tray is back!!!
But I'm stil eager to see any other dev of wp changer!

I don't know why, but I can no longer 'make' wp_tray. On the homepage he states that there are problems with schemas. That's exactly my problem. I hope it gets resolved soon[/QUOTE]
 All the links to the .deb files are dead too.

---

### Post by Sam on 2005-07-25
[QUOTE=poptones]```

#!/bin/bash
WALLPAPERS="/home/poptones/wallpapers" #change this path for your system
ALIST=( `ls -w1 wallpapers` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat $WALLPAPERS/.last` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

```

Save this in a /home/username/wallpapers/ directory as ".randomwallpaper.sh" and make a panel launcher to it with this in the command:

sh /home/*username*/wallpapers/.randomwallpaper.sh

Mine sits right next to my clock, a single click toggles the wallpaper. You can make it run on a cron task if oyu like or you could just add a "sleep *delay*" line to the end.[/QUOTE]
You should write an howto for this ! :wink:

---

### Post by rwabel on 2005-07-26
[QUOTE=pt123]All the links to the .deb files are dead too.[/QUOTE]
 and for 0.5 there aren't any debs at all :-(
I suggest you download 0.46 and compile it by yourself. There is a ubuntu one, but it doesn't work for hoary, because of dependencies.
0.46 works fine, it's just not an applet

---

### Post by pt123 on 2005-07-27
[QUOTE=rwabel]and for 0.5 there aren't any debs at all :-(
I suggest you download 0.46 and compile it by yourself. There is a ubuntu one, but it doesn't work for hoary, because of dependencies.
0.46 works fine, it's just not an applet[/QUOTE]
 The 0.46 link to the tar file is dead, can you please post the file somewhere?

---

### Post by rwabel on 2005-07-27
[QUOTE=pt123]The 0.46 link to the tar file is dead, can you please post the file somewhere?[/QUOTE]
 there was a link in preview post with the files. Here you go: [http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/)

---

### Post by Ken.Lank on 2005-07-27
OK, well I've figured out the code on my own ... I have made some mods and changed a couple of things to make it more readable to me .. I'll post it up in case it can help someone else out or you want to see my changes.

```
#!/bin/bash

strDir="/home/klank/Wallpapers"
aryFiles=( `ls -w1 $strDir` )
intLastNum=$[ `cat $strDir/.Last_Wallpaper` + 0 ]
intNumFiles=${#aryFiles[@]}
intRandomNum=$[ (($RANDOM % $intNumFiles) + $intLastNum) % $intNumFiles ]
echo $intRandomNum > $strDir/.Last_Wallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $strDir/${aryFiles[$intRandomNum]}

```

---

### Post by geraldo5002 on 2005-07-27
My mono applet has a small gui now. 

You can:

- Choose the dir where the wallpapers are (it's recursive and filenames can contain spaces);
- Activate/Deactivate timed changes;
- Set the interval between timed changes;
- Change wallpaper on a single click;

It was written using mono and gtk#.

I dont know how to create a .deb file yet, but i can send the file to anyone who wishes to try it. It works very well in my system (for about two days now) changing the wallpaper at each 5 minutes. 

If someone would like to try it, let me now (geraldo5002 at gmail dot com).

---

### Post by rwabel on 2005-07-27
[QUOTE=geraldo5002]My mono applet has a small gui now. 

You can:

- Choose the dir where the wallpapers are (it's recursive and filenames can contain spaces);
- Activate/Deactivate timed changes;
- Set the interval between timed changes;
- Change wallpaper on a single click;

It was written using mono and gtk#.

I dont know how to create a .deb file yet, but i can send the file to anyone who wishes to try it. It works very well in my system (for about two days now) changing the wallpaper at each 5 minutes. 

If someone would like to try it, let me now (geraldo5002 at gmail dot com).[/QUOTE]
 why not attach the source to the message, in that case everyone can try it

---

### Post by geraldo5002 on 2005-07-27
I've used monodevelop. It compiled fine there, but using the command line is giving me some strange errors. It's strange, because it seems to be using the same options.

As soons as I discover the command line options I'll post it.

I need to figure out how to use gtk-sharp 2.0 in comand line

---

### Post by geraldo5002 on 2005-07-27
Code is messy. I'll chean up later. There're 3 files. WPSwitcher.cs, TrayLib.cs and gui.glade. Command line to compile is at the end. Run the program and it will apear as a icon on your notification area. Post any problems and I'll try to solve.

File WPSwitcher.cs

// WPSwitcher.cs -------------------------------------
using Gtk;
using GLib;
using System;
using System.IO;
using System.Collections;
using GConf;
using Glade;
using System.Threading;
 
public class WPSwitcher
{
	// UI Widgets
    [Widget]
    Window MainWindow;
    [Widget]
    Entry entry1;
    [Widget]
    CheckButton	checkbutton1;
    [Widget]
    SpinButton	spinbutton1;
    
	// Configuration    
	GConf.Client client = new GConf.Client();
	    
	// Default config    
	static string GCONF_APP_PATH = "/apps/WPSwitcher";
	static string FOLDER_KEY = GCONF_APP_PATH + System.Environment.GetEnvironmentVariable("HOME");
	static string INTERVAL_KEY = GCONF_APP_PATH + "/interval";
	static string TIMED_KEY = GCONF_APP_PATH + "/use_timed";
    
	// Wallpaper list  
	ArrayList fileList = new ArrayList();

	// Data used in the program
	string	wallpaperPath = System.Environment.GetEnvironmentVariable("HOME");
	int		tickInterval = 1;
	bool	timedInterval = false;
	
	// Timer data
	Timer timer;
	

	void CheckStatus(object state)
	{
		if(timedInterval) FindAndSet();
	}

	public static void Main()
	{
		// initialises the application
		Application.Init();
		
		
		WPSwitcher test = new WPSwitcher();
		
		

		// runs application
		Application.Run();
	}
	
	void UpdateFromGConf ()
	{
		try {
			wallpaperPath = (string) client.Get (FOLDER_KEY);
			tickInterval = (int) client.Get (INTERVAL_KEY);			
			timedInterval = (bool) client.Get (TIMED_KEY);
		} catch (GConf.NoSuchKeyException e) {
			Console.WriteLine("Error: A key with that name doesn't exist.");
			// add your exception handling here
		} catch (System.InvalidCastException e) {
			Console.WriteLine("Error: Cannot typecast.");
			// add your exception handling here
		}
	}
	
	
	void UpdateToGConf ()
	{
		try {
		    client.Set (FOLDER_KEY, wallpaperPath);
		    client.Set (INTERVAL_KEY, tickInterval);
			client.Set (TIMED_KEY,timedInterval);		    
		} catch (GConf.NoSuchKeyException e) {
			Console.WriteLine("Error: A key with that name doesn't exist.");
			// add your exception handling here
		} catch (System.InvalidCastException e) {
			Console.WriteLine("Error: Cannot typecast.");
			// add your exception handling here
		}
	}	
		

   	// Gets the start point and starts the search for pictures.
   	public void ListRecursive(string location, string type)
   	{
		System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(location);
		ListFolders(dir,type);
   	}
   	
   	
   	// Adds files from dir matching type to the fileList. Used only in 
   	// ListFolders
   	public void ListFiles(System.IO.DirectoryInfo dir, string type)
   	{
   		System.IO.FileInfo[] files;
   		
   		try {
   			files = dir.GetFiles(type);
		    foreach (System.IO.FileInfo f in files )
	   		{	
				fileList.Add( dir.FullName + "/" + f.Name );			
	   		}   	
		} catch (System.UnauthorizedAccessException e) {
			Console.WriteLine("Access to directory denied.");
		}
   	}
	
	// Adds files from dir matching type AND folders to the fileList
	public void ListFolders(System.IO.DirectoryInfo dir, string type)
   	{
   		ListFiles( dir, type );
   		try {
	   		DirectoryInfo[] directoryInfo = dir.GetDirectories();
	    	foreach (System.IO.DirectoryInfo g in directoryInfo) 
	    	{    
		       	ListFiles(g,type);
		       	ListFolders(g,type);
	        } 	    
	   	} catch (System.UnauthorizedAccessException e) {
			Console.WriteLine("Access to directory denied.");
	   	}
   	}
   	
	// Just for debuging...Glade.XML gxml
   	public void PrintFileList()
   	{
	    	foreach (string str in fileList) 
    		{
    			Console.WriteLine( str );    
        	} 	    
   	}
   	
	// Chooses a random pictures and sets it as wallpaper
   	public void SetRandomWallpaper()
   	{
   		if(fileList.Count > 0 ) 
   		{
			GConf.Client gclient = new GConf.Client();
			Random random = new Random();
			gclient.Set("/desktop/gnome/background/picture_filename", fileList[random.Next() % fileList.Count]);	    
        	gclient.SuggestSync();
        }
   	}

	public void FindAndSet() 
	{
		fileList.Clear();
		ListRecursive(wallpaperPath,"*jpg");
		SetRandomWallpaper();
	}

 
	public WPSwitcher()
	{
		//MainWindow.Hide();	
		/* in order to receive signals, we need a eventbox,
                because Gtk.Image doesn't receive signals */
		EventBox eb = new EventBox();
		eb.Add(new Image(Stock.Yes, IconSize.Menu)); // using stock icon
		// hooking event
		eb.ButtonPressEvent += new ButtonPressEventHandler (this.OnImageClick);
		Egg.TrayIcon icon = new Egg.TrayIcon("MainWindow");
		icon.Add(eb);
		// showing the trayicon
		icon.ShowAll();
		
		UpdateFromGConf();

		TimerCallback timerDelegate = new TimerCallback(CheckStatus);
		
		timer = new Timer(timerDelegate, null,tickInterval*1000,tickInterval*1000);
		
		
	}
	
	private void OnImageClick (object o, ButtonPressEventArgs args) // handler for mouse click
	{
   		if (args.Event.Button == 3) //right click
   		{
      			Menu popupMenu = new Menu(); // creates the menu  


                	// creates a menu item with no image as default
      			ImageMenuItem menuPopup2 = new ImageMenuItem ("Refresh");

                	// creates a image for the menu item
      			Image appimg2 = new Image(Stock.Refresh, IconSize.Menu);
      			menuPopup2.Image = appimg2; // sets the menu item's image
      			popupMenu.Add(menuPopup2); // adds the menu item to the menu
	                // hooks a event when the user clicks the icon
	      		menuPopup2.Activated += new EventHandler(this.OnReload);


                	// creates a menu item with no image as default
      			ImageMenuItem menuPopup3 = new ImageMenuItem ("Properties");

                	// creates a image for the menu item
      			Image appimg3 = new Image(Stock.Properties, IconSize.Menu);
      			menuPopup3.Image = appimg3; // sets the menu item's image
      			popupMenu.Add(menuPopup3); // adds the menu item to the menu
	                // hooks a event when the user clicks the icon
	      		menuPopup3.Activated += new EventHandler(this.OnProperties);


               	// creates a menu item with no image as default
      			ImageMenuItem menuPopup31 = new ImageMenuItem ("About");

                	// creates a image for the menu item
      			Image appimg31 = new Image(Stock.Help, IconSize.Menu);
      			menuPopup31.Image = appimg31; // sets the menu item's image
      			popupMenu.Add(menuPopup31); // adds the menu item to the menu
	                // hooks a event when the user clicks the icon
	      		menuPopup31.Activated += new EventHandler(this.OnAbout);



                	// creates a menu item with no image as default
      			ImageMenuItem menuPopup1 = new ImageMenuItem ("Quit");

                	// creates a image for the menu item
      			Image appimg = new Image(Stock.Quit, IconSize.Menu);
      			menuPopup1.Image = appimg; // sets the menu item's image
      			popupMenu.Add(menuPopup1); // adds the menu item to the menu
	                // hooks a event when the user clicks the icon
	      		menuPopup1.Activated += new EventHandler(this.OnQuit);

				popupMenu.ShowAll(); // shows everything
	                // pops up the actual menu when the user right clicks
	      		popupMenu.Popup(null, null, null, IntPtr.Zero, args.Event.Button, args.Event.Time);
   		}
   		if (args.Event.Button == 1) //left click
		{
			FindAndSet();
		}
	}
	private void OnQuit(object o, EventArgs args)
	{
		Application.Quit(); // quits the application when the users clicks the popup menu
	}

	private void OnReload(object o, EventArgs args)
	{
		FindAndSet() ;
	}
	private void OnProperties(object o, EventArgs args)
	{
        Glade.XML gxml = new Glade.XML(null,"gui.glade", "MainWindow", null);
        gxml.Autoconnect (this);
        entry1.Text = wallpaperPath;
        spinbutton1.Value = tickInterval;
        checkbutton1.Active = timedInterval;
	}
	
	private void OnAbout(object o, EventArgs args)
	{
		string[] authors = new string [] {
			"Geraldo Dal Berto Jr. (geraldo5002@gmail.com)",
		};
		
		string [] documenters = new string [] {};
		string translaters = null;
		
		Gnome.About about = new Gnome.About ("WPSwitcher", "0.1",
						 "Copyright 2005 Geraldo Dal Berto Jr.",
						 "Switches the wallpaper to a random one inside a specified folder.",
						     authors, documenters, translaters,
						     null);
		about.Show ();
	}

   	public void on_WPSwitcher_delete_event( object o, EventArgs e)
   	{
   		Console.WriteLine("on_delete1");
   		MainWindow.Hide();
   	}	

   	public void on_button5_clicked( object o, EventArgs e)
   	{
 		Gtk.FileChooserDialog fs = new Gtk.FileChooserDialog("Choose folder", Gtk.Stock.Open,null, FileChooserAction.Open);
 		fs.AddButton(Gtk.Stock.Ok, Gtk.ResponseType.Cancel);
 		fs.AddButton (Gtk.Stock.Close, Gtk.ResponseType.Close); 
   		fs.Run();
   		entry1.Text = fs.CurrentFolder;
   		fs.Destroy();
   		FindAndSet();
   	}
   	public void on_button3_clicked( object o, EventArgs e)
   	{
   		MainWindow.Hide();
   	}
   	public void on_button4_clicked( object o, EventArgs e)
   	{
 		wallpaperPath = entry1.Text;
        tickInterval = (int)spinbutton1.Value;
        timedInterval = checkbutton1.Active;
        timer.Change(tickInterval*1000,tickInterval*1000);
        
        UpdateToGConf();
   		MainWindow.Hide();        
   	}
}

/// File TrayLib.cs --------------------------------------------
/*
I didnt touch this file (except this comment) 
*/

using System;
using System.Runtime.InteropServices;
 
using Gtk;
using Gdk;
 
namespace Egg
{
	public class TrayIcon : Plug
	{
		int stamp;
		Orientation orientation;
		
		int selection_atom;
		int manager_atom;
		int system_tray_opcode_atom;
		int orientation_atom;
		IntPtr manager_window;
		FilterFunc filter;
		
		public TrayIcon (string name)
		{
			Title = name;
			stamp = 1;
			orientation = Orientation.Horizontal;
			AddEvents ((int)EventMask.PropertyChangeMask);
			filter = new FilterFunc (ManagerFilter);
		}
 
		protected override void OnRealized ()
		{
			base.OnRealized ();
			Display display = Screen.Display;
			IntPtr xdisplay = gdk_x11_display_get_xdisplay (display.Handle);
			selection_atom = XInternAtom (xdisplay, "_NET_SYSTEM_TRAY_S" + Screen.Number.ToString (), false);
			manager_atom = XInternAtom (xdisplay, "MANAGER", false);
			system_tray_opcode_atom = XInternAtom (xdisplay, "_NET_SYSTEM_TRAY_OPCODE", false);
			orientation_atom = XInternAtom (xdisplay, "_NET_SYSTEM_TRAY_ORIENTATION", false);
			UpdateManagerWindow ();
			//Screen.RootWindow.AddFilter (filter);
		}
 
		protected override void OnUnrealized ()
		{
			if (manager_window != IntPtr.Zero)
			{
				Gdk.Window gdkwin = Gdk.Window.LookupForDisplay (Display, (uint)manager_window);
				//gdkwin.RemoveFilter (filter);
			}
			
			//Screen.RootWindow.RemoveFilter (filter);
			base.OnUnrealized ();
		}
 
		private void UpdateManagerWindow ()
		{
			IntPtr xdisplay = gdk_x11_display_get_xdisplay (Display.Handle);
			if (manager_window != IntPtr.Zero)
			{
				Gdk.Window gdkwin = Gdk.Window.LookupForDisplay (Display, (uint)manager_window);
				//gdkwin.RemoveFilter (filter);
			}
 
			XGrabServer (xdisplay);
 
			manager_window = XGetSelectionOwner (xdisplay, selection_atom);
			if (manager_window != IntPtr.Zero)
				XSelectInput (xdisplay, manager_window, EventMask.StructureNotifyMask | EventMask.PropertyChangeMask);
			XUngrabServer (xdisplay);
			XFlush (xdisplay);
 
			if (manager_window != IntPtr.Zero) {
				Gdk.Window gdkwin = Gdk.Window.LookupForDisplay (Display, (uint)manager_window);
				//gdkwin.AddFilter (filter);
				SendDockRequest ();
				GetOrientationProperty ();
			}
		}
 
		private void SendDockRequest ()
		{
			SendManagerMessage (SystemTrayMessage.RequestDock, manager_window, Id, 0, 0);
		}
 
		private void SendManagerMessage (SystemTrayMessage message, IntPtr window, uint data1, uint data2, uint data3)
		{
			XClientMessageEvent ev = new XClientMessageEvent ();
			IntPtr display;
 
			ev.type = XEventName.ClientMessage;
			ev.window = window;
			ev.message_type = (IntPtr)system_tray_opcode_atom;
			ev.format = 32;
			ev.ptr1 = gdk_x11_get_server_time (GdkWindow.Handle);
			ev.ptr2 = (IntPtr)message;
			ev.ptr3 = (IntPtr)data1;
			ev.ptr4 = (IntPtr)data2;
			ev.ptr5 = (IntPtr)data3;
 
			display = gdk_x11_display_get_xdisplay (Display.Handle);
			gdk_error_trap_push ();
			XSendEvent (display, manager_window, false, EventMask.NoEventMask, ref ev);
			gdk_error_trap_pop ();
		}
 
		private FilterReturn ManagerFilter (IntPtr xevent, Event evnt)
		{
			//TODO: Implement;
			return FilterReturn.Continue;
		}
 
		private void GetOrientationProperty ()
		{
			//TODO: Implement;
		}
 
		[DllImport ("gdk-x11-2.0")]
		static extern IntPtr gdk_x11_display_get_xdisplay (IntPtr display);
		[DllImport ("gdk-x11-2.0")]
		static extern IntPtr gdk_x11_get_server_time (IntPtr window);
		[DllImport ("gdk-x11-2.0")]
		static extern void gdk_error_trap_push ();
		[DllImport ("gdk-x11-2.0")]
		static extern void gdk_error_trap_pop ();
		
		[DllImport ("libX11", EntryPoint="XInternAtom")]
		extern static int XInternAtom(IntPtr display, string atom_name, bool only_if_exists);
		[DllImport ("libX11")]
		extern static void XGrabServer (IntPtr display);
		[DllImport ("libX11")]
		extern static void XUngrabServer (IntPtr display);
		[DllImport ("libX11")]
		extern static int XFlush (IntPtr display);
		[DllImport ("libX11")]
		extern static IntPtr XGetSelectionOwner (IntPtr display, int atom);
		[DllImport ("libX11")]
		extern static IntPtr XSelectInput (IntPtr window, IntPtr display, EventMask mask);
		[DllImport ("libX11", EntryPoint="XSendEvent")]
		extern static int XSendEvent(IntPtr display, IntPtr window, bool propagate, EventMask event_mask, ref XClientMessageEvent send_event);
	}
 
	[Flags]
	internal enum EventMask {
		NoEventMask             = 0,
		KeyPressMask            = 1<<0,
		KeyReleaseMask          = 1<<1,
		ButtonPressMask         = 1<<2,
		ButtonReleaseMask       = 1<<3,
		EnterWindowMask         = 1<<4,
		LeaveWindowMask         = 1<<5,
		PointerMotionMask       = 1<<6,
		PointerMotionHintMask   = 1<<7,
		Button1MotionMask       = 1<<8,
		Button2MotionMask       = 1<<9,
		Button3MotionMask       = 1<<10,
		Button4MotionMask       = 1<<11,
		Button5MotionMask       = 1<<12,
		ButtonMotionMask        = 1<<13,
		KeymapStateMask         = 1<<14,
		ExposureMask            = 1<<15,
		VisibilityChangeMask    = 1<<16,
		StructureNotifyMask     = 1<<17,
		ResizeRedirectMask      = 1<<18,
                SubstructureNotifyMask  = 1<<19,
		SubstructureRedirectMask= 1<<20,
		FocusChangeMask         = 1<<21,
		PropertyChangeMask      = 1<<22,
		ColormapChangeMask      = 1<<23,
		OwnerGrabButtonMask     = 1<<24
	}
 
	internal enum SystemTrayMessage
	{
		RequestDock,
		BeginMessage,
		CancelMessage
	}
 
	internal enum SystemTrayOrientation
	{
		Horz,
		Vert
	}
	
	[StructLayout(LayoutKind.Sequential)]
	internal struct XClientMessageEvent {
		internal XEventName     type;
		internal int            serial;
		internal bool           send_event;
		internal IntPtr         display;
		internal IntPtr         window;
		internal IntPtr         message_type;
		internal int            format;
		internal IntPtr         ptr1;
		internal IntPtr         ptr2;
		internal IntPtr         ptr3;
		internal IntPtr         ptr4;
		internal IntPtr         ptr5;
	}
 
	internal enum XEventName {
		KeyPress                = 2,
		KeyRelease              = 3,
		ButtonPress             = 4,
		ButtonRelease           = 5,
		MotionNotify            = 6,
		EnterNotify             = 7,
		LeaveNotify             = 8,
		FocusIn                 = 9,
		FocusOut                = 10,
		KeymapNotify            = 11,
		Expose                  = 12,
		GraphicsExpose          = 13,
		NoExpose                = 14,
		VisibilityNotify        = 15,
		CreateNotify            = 16,
		DestroyNotify           = 17,
		UnmapNotify             = 18,
		MapNotify               = 19,
		MapRequest              = 20,
		ReparentNotify          = 21,
		ConfigureNotify         = 22,
		ConfigureRequest        = 23,
		GravityNotify           = 24,
		ResizeRequest           = 25,
		CirculateNotify         = 26,
		CirculateRequest        = 27,
		PropertyNotify          = 28,
		SelectionClear          = 29,
		SelectionRequest        = 30,
		SelectionNotify         = 31,
		ColormapNotify          = 32,
		ClientMessage           = 33,
		MappingNotify           = 34,
		TimerNotify             = 100,
		
		LASTEvent
	}
}
[\CODE]

/// gui.glade ----------------------------------------------------------

<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>

<widget class="GtkWindow" id="MainWindow">
  <property name="visible">True</property>
  <property name="title" translatable="yes">WPSwitcher</property>
  <property name="type">GTK_WINDOW_TOPLEVEL</property>
  <property name="window_position">GTK_WIN_POS_MOUSE</property>
  <property name="modal">False</property>
  <property name="resizable">True</property>
  <property name="destroy_with_parent">False</property>
  <property name="decorated">True</property>
  <property name="skip_taskbar_hint">False</property>
  <property name="skip_pager_hint">False</property>
  <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
  <property name="gravity">GDK_GRAVITY_NORTH_WEST</property>
  <property name="focus_on_map">True</property>
  <signal name="delete_event" handler="on_WPSwitcher_delete_event" last_modification_time="Tue, 26 Jul 2005 21:04:55 GMT"/>

  <child>
    <widget class="GtkVBox" id="vbox1">
      <property name="border_width">8</property>
      <property name="visible">True</property>
      <property name="homogeneous">False</property>
      <property name="spacing">0</property>

      <child>
	<widget class="GtkVBox" id="vbox3">
	  <property name="visible">True</property>
	  <property name="homogeneous">False</property>
	  <property name="spacing">0</property>

	  <child>
	    <widget class="GtkHBox" id="hbox8">
	      <property name="visible">True</property>
	      <property name="homogeneous">False</property>
	      <property name="spacing">0</property>

	      <child>
		<widget class="GtkLabel" id="label8">
		  <property name="visible">True</property>
		  <property name="label" translatable="yes">Wallpaper Folder  </property>
		  <property name="use_underline">False</property>
		  <property name="use_markup">False</property>
		  <property name="justify">GTK_JUSTIFY_LEFT</property>
		  <property name="wrap">False</property>
		  <property name="selectable">False</property>
		  <property name="xalign">0.5</property>
		  <property name="yalign">0.5</property>
		  <property name="xpad">0</property>
		  <property name="ypad">0</property>
		  <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
		  <property name="width_chars">-1</property>
		  <property name="single_line_mode">False</property>
		  <property name="angle">0</property>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">False</property>
		  <property name="fill">False</property>
		</packing>
	      </child>

	      <child>
		<widget class="GtkEntry" id="entry1">
		  <property name="visible">True</property>
		  <property name="can_focus">True</property>
		  <property name="editable">True</property>
		  <property name="visibility">True</property>
		  <property name="max_length">0</property>
		  <property name="text" translatable="yes">/home/geraldo/Images/wallpaper</property>
		  <property name="has_frame">True</property>
		  <property name="invisible_char">*</property>
		  <property name="activates_default">False</property>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">True</property>
		  <property name="fill">True</property>
		</packing>
	      </child>

	      <child>
		<widget class="GtkButton" id="button5">
		  <property name="visible">True</property>
		  <property name="can_focus">True</property>
		  <property name="label" translatable="yes">...</property>
		  <property name="use_underline">True</property>
		  <property name="relief">GTK_RELIEF_NORMAL</property>
		  <property name="focus_on_click">True</property>
		  <signal name="clicked" handler="on_button5_clicked" last_modification_time="Tue, 26 Jul 2005 23:27:46 GMT"/>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">False</property>
		  <property name="fill">False</property>
		</packing>
	      </child>
	    </widget>
	    <packing>
	      <property name="padding">16</property>
	      <property name="expand">False</property>
	      <property name="fill">False</property>
	    </packing>
	  </child>

	  <child>
	    <widget class="GtkHBox" id="hbox10">
	      <property name="visible">True</property>
	      <property name="homogeneous">False</property>
	      <property name="spacing">0</property>

	      <child>
		<widget class="GtkCheckButton" id="checkbutton1">
		  <property name="visible">True</property>
		  <property name="can_focus">True</property>
		  <property name="label" translatable="yes">Timed change</property>
		  <property name="use_underline">True</property>
		  <property name="relief">GTK_RELIEF_NORMAL</property>
		  <property name="focus_on_click">True</property>
		  <property name="active">True</property>
		  <property name="inconsistent">False</property>
		  <property name="draw_indicator">True</property>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">True</property>
		  <property name="fill">True</property>
		</packing>
	      </child>

	      <child>
		<widget class="GtkHBox" id="hbox11">
		  <property name="visible">True</property>
		  <property name="homogeneous">False</property>
		  <property name="spacing">0</property>

		  <child>
		    <widget class="GtkLabel" id="label10">
		      <property name="visible">True</property>
		      <property name="label" translatable="yes">Interval (secs) </property>
		      <property name="use_underline">False</property>
		      <property name="use_markup">False</property>
		      <property name="justify">GTK_JUSTIFY_LEFT</property>
		      <property name="wrap">False</property>
		      <property name="selectable">False</property>
		      <property name="xalign">0.5</property>
		      <property name="yalign">0.5</property>
		      <property name="xpad">0</property>
		      <property name="ypad">0</property>
		      <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
		      <property name="width_chars">-1</property>
		      <property name="single_line_mode">False</property>
		      <property name="angle">0</property>
		    </widget>
		    <packing>
		      <property name="padding">0</property>
		      <property name="expand">False</property>
		      <property name="fill">False</property>
		    </packing>
		  </child>

		  <child>
		    <widget class="GtkSpinButton" id="spinbutton1">
		      <property name="visible">True</property>
		      <property name="can_focus">True</property>
		      <property name="climb_rate">1</property>
		      <property name="digits">0</property>
		      <property name="numeric">False</property>
		      <property name="update_policy">GTK_UPDATE_ALWAYS</property>
		      <property name="snap_to_ticks">False</property>
		      <property name="wrap">False</property>
		      <property name="adjustment">5 1 1000000 1 10 10</property>
		    </widget>
		    <packing>
		      <property name="padding">0</property>
		      <property name="expand">True</property>
		      <property name="fill">True</property>
		    </packing>
		  </child>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">True</property>
		  <property name="fill">True</property>
		</packing>
	      </child>
	    </widget>
	    <packing>
	      <property name="padding">0</property>
	      <property name="expand">True</property>
	      <property name="fill">True</property>
	    </packing>
	  </child>

	  <child>
	    <widget class="GtkLabel" id="label11">
	      <property name="visible">True</property>
	      <property name="label" translatable="yes"></property>
	      <property name="use_underline">False</property>
	      <property name="use_markup">False</property>
	      <property name="justify">GTK_JUSTIFY_LEFT</property>
	      <property name="wrap">False</property>
	      <property name="selectable">False</property>
	      <property name="xalign">0.5</property>
	      <property name="yalign">0.5</property>
	      <property name="xpad">0</property>
	      <property name="ypad">0</property>
	      <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
	      <property name="width_chars">-1</property>
	      <property name="single_line_mode">False</property>
	      <property name="angle">0</property>
	    </widget>
	    <packing>
	      <property name="padding">17</property>
	      <property name="expand">False</property>
	      <property name="fill">False</property>
	    </packing>
	  </child>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">True</property>
	  <property name="fill">True</property>
	</packing>
      </child>

      <child>
	<widget class="GtkHBox" id="hbox1">
	  <property name="visible">True</property>
	  <property name="homogeneous">True</property>
	  <property name="spacing">0</property>

	  <child>
	    <widget class="GtkButton" id="button3">
	      <property name="visible">True</property>
	      <property name="can_focus">True</property>
	      <property name="label">gtk-cancel</property>
	      <property name="use_stock">True</property>
	      <property name="relief">GTK_RELIEF_NORMAL</property>
	      <property name="focus_on_click">True</property>
	      <signal name="clicked" handler="on_button3_clicked" last_modification_time="Wed, 27 Jul 2005 01:23:42 GMT"/>
	    </widget>
	    <packing>
	      <property name="padding">0</property>
	      <property name="expand">True</property>
	      <property name="fill">True</property>
	    </packing>
	  </child>

	  <child>
	    <widget class="GtkLabel" id="label12">
	      <property name="visible">True</property>
	      <property name="label" translatable="yes"></property>
	      <property name="use_underline">False</property>
	      <property name="use_markup">False</property>
	      <property name="justify">GTK_JUSTIFY_LEFT</property>
	      <property name="wrap">False</property>
	      <property name="selectable">False</property>
	      <property name="xalign">0.5</property>
	      <property name="yalign">0.5</property>
	      <property name="xpad">0</property>
	      <property name="ypad">0</property>
	      <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
	      <property name="width_chars">-1</property>
	      <property name="single_line_mode">False</property>
	      <property name="angle">0</property>
	    </widget>
	    <packing>
	      <property name="padding">0</property>
	      <property name="expand">False</property>
	      <property name="fill">False</property>
	    </packing>
	  </child>

	  <child>
	    <widget class="GtkButton" id="button4">
	      <property name="visible">True</property>
	      <property name="can_focus">True</property>
	      <property name="label">gtk-ok</property>
	      <property name="use_stock">True</property>
	      <property name="relief">GTK_RELIEF_NORMAL</property>
	      <property name="focus_on_click">True</property>
	      <signal name="clicked" handler="on_button4_clicked" last_modification_time="Wed, 27 Jul 2005 01:23:37 GMT"/>
	    </widget>
	    <packing>
	      <property name="padding">0</property>
	      <property name="expand">True</property>
	      <property name="fill">True</property>
	    </packing>
	  </child>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">True</property>
	</packing>
      </child>
    </widget>
  </child>
</widget>

</glade-interface>




Build with:

mcs -pkg:gtk-sharp-2.0,gconf-sharp,glade-sharp,gnome-sharp -resource:gui.glade WPSwitcher.cs TrayLib.cs

---

### Post by pt123 on 2005-07-27
[QUOTE=rwabel]there was a link in preview post with the files. Here you go: [http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/)[/QUOTE]

Thanks a lot

----
Can someone please make a deb file out of Geraldos code?

---

### Post by geraldo5002 on 2005-07-28
Has anyone tried it? It worked? Any bugs? What do you think? 

Feedback would be nice.... :-)

---

### Post by ubuntp on 2005-07-28
It doesn't seem to run here, all i get is:

Unhandled Exception: System.DllNotFoundException: gdk-x11-2.0
in (wrapper managed-to-native) Egg.TrayIcon:gdk_x11_display_get_xdisplay (intptr)

Some library must be missing, which one.

---

### Post by geraldo5002 on 2005-07-28
Well, hell begins here...

The dependencies make sofware deploying in linux are a real pain...

Well... I have several mono apps running im my system (muine, tomboy, f-spot, blam). So synaptic installed automagically the libs from mono runtime.

I guess the missing lib is libgtk2.0-cil, but that is just a guess.

I searched for that gdk file, but haven't found any. The error message from the runtime is not usefull at all...

Sorry... I'l try to find what is going wrong here...

---

### Post by ubuntp on 2005-07-28
I got f-spot and beagle running as well, also libgtk2.0-cil is installed (that was my first guess too). I'm using Breezy though.

---

### Post by rwabel on 2005-07-29
[QUOTE=geraldo5002]Has anyone tried it? It worked? Any bugs? What do you think? 

Feedback would be nice.... :-)[/QUOTE]

Compilation had 9 warnings but did work. I could start it, but there was also a little error: ```
Error: A key with that name doesn't exist.
```.

Furtheremore, I get Acces to directory denied. 

When I click on preferences I get the following error and the program crashes:
```
(<unknown>:18181): XML-CRITICAL **: Start tag expected, '<' not found


(<unknown>:18181): libglade-WARNING **: did not finish in PARSER_FINISH state!

(<unknown>:18181): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(<unknown>:18181): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(<unknown>:18181): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(<unknown>:18181): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(<unknown>:18181): libglade-CRITICAL **: glade_xml_signal_autoconnect_full: assertion `self != NULL' failed

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00046> WPSwitcher:OnProperties (System.Object o, System.EventArgs args)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
in <0x00096> GLib.Signal:voidObjectCallback (IntPtr handle, IntPtr gch)
in (wrapper native-to-managed) GLib.Signal:voidObjectCallback (intptr,intptr)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0002e> WPSwitcher:Main ()
```

---

### Post by geraldo5002 on 2005-07-29
Seems like file gui.glade is bad. 

The warning messages are mostly from file TrayLib.cs which I downloaded from mono site. I didn't touch that file. It provides the methods to put the icon on the tray. I got those warning's too, but the program runs fine...

Check your gui.glade to see if is complete...

That key message doens't stop the program from run. It only apears the first time you run. I guess if you check the gui.glade and try to compile again it will work.

If you run into problems, let me know...

---

### Post by rwabel on 2005-07-29
[QUOTE=geraldo5002]Seems like file gui.glade is bad. 

The warning messages are mostly from file TrayLib.cs which I downloaded from mono site. I didn't touch that file. It provides the methods to put the icon on the tray. I got those warning's too, but the program runs fine...

Check your gui.glade to see if is complete...

That key message doens't stop the program from run. It only apears the first time you run. I guess if you check the gui.glade and try to compile again it will work.

If you run into problems, let me know...[/QUOTE]

It should be complet. I copied twice from your post:
```
<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>

<widget class="GtkWindow" id="MainWindow">
<property name="visible">True</property>
<property name="title" translatable="yes">WPSwitcher</property>
<property name="type">GTK_WINDOW_TOPLEVEL</property>
<property name="window_position">GTK_WIN_POS_MOUSE</property>
<property name="modal">False</property>
<property name="resizable">True</property>
<property name="destroy_with_parent">False</property>
<property name="decorated">True</property>
<property name="skip_taskbar_hint">False</property>
<property name="skip_pager_hint">False</property>
<property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
<property name="gravity">GDK_GRAVITY_NORTH_WEST</property>
<property name="focus_on_map">True</property>
<signal name="delete_event" handler="on_WPSwitcher_delete_event" last_modification_time="Tue, 26 Jul 2005 21:04:55 GMT"/>

<child>
<widget class="GtkVBox" id="vbox1">
<property name="border_width">8</property>
<property name="visible">True</property>
<property name="homogeneous">False</property>
<property name="spacing">0</property>

<child>
<widget class="GtkVBox" id="vbox3">
<property name="visible">True</property>
<property name="homogeneous">False</property>
<property name="spacing">0</property>

<child>
<widget class="GtkHBox" id="hbox8">
<property name="visible">True</property>
<property name="homogeneous">False</property>
<property name="spacing">0</property>

<child>
<widget class="GtkLabel" id="label8">
<property name="visible">True</property>
<property name="label" translatable="yes">Wallpaper Folder </property>
<property name="use_underline">False</property>
<property name="use_markup">False</property>
<property name="justify">GTK_JUSTIFY_LEFT</property>
<property name="wrap">False</property>
<property name="selectable">False</property>
<property name="xalign">0.5</property>
<property name="yalign">0.5</property>
<property name="xpad">0</property>
<property name="ypad">0</property>
<property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
<property name="width_chars">-1</property>
<property name="single_line_mode">False</property>
<property name="angle">0</property>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">False</property>
<property name="fill">False</property>
</packing>
</child>

<child>
<widget class="GtkEntry" id="entry1">
<property name="visible">True</property>
<property name="can_focus">True</property>
<property name="editable">True</property>
<property name="visibility">True</property>
<property name="max_length">0</property>
<property name="text" translatable="yes">/home/geraldo/Images/wallpaper</property>
<property name="has_frame">True</property>
<property name="invisible_char">*</property>
<property name="activates_default">False</property>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>

<child>
<widget class="GtkButton" id="button5">
<property name="visible">True</property>
<property name="can_focus">True</property>
<property name="label" translatable="yes">...</property>
<property name="use_underline">True</property>
<property name="relief">GTK_RELIEF_NORMAL</property>
<property name="focus_on_click">True</property>
<signal name="clicked" handler="on_button5_clicked" last_modification_time="Tue, 26 Jul 2005 23:27:46 GMT"/>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">False</property>
<property name="fill">False</property>
</packing>
</child>
</widget>
<packing>
<property name="padding">16</property>
<property name="expand">False</property>
<property name="fill">False</property>
</packing>
</child>

<child>
<widget class="GtkHBox" id="hbox10">
<property name="visible">True</property>
<property name="homogeneous">False</property>
<property name="spacing">0</property>

<child>
<widget class="GtkCheckButton" id="checkbutton1">
<property name="visible">True</property>
<property name="can_focus">True</property>
<property name="label" translatable="yes">Timed change</property>
<property name="use_underline">True</property>
<property name="relief">GTK_RELIEF_NORMAL</property>
<property name="focus_on_click">True</property>
<property name="active">True</property>
<property name="inconsistent">False</property>
<property name="draw_indicator">True</property>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>

<child>
<widget class="GtkHBox" id="hbox11">
<property name="visible">True</property>
<property name="homogeneous">False</property>
<property name="spacing">0</property>

<child>
<widget class="GtkLabel" id="label10">
<property name="visible">True</property>
<property name="label" translatable="yes">Interval (secs) </property>
<property name="use_underline">False</property>
<property name="use_markup">False</property>
<property name="justify">GTK_JUSTIFY_LEFT</property>
<property name="wrap">False</property>
<property name="selectable">False</property>
<property name="xalign">0.5</property>
<property name="yalign">0.5</property>
<property name="xpad">0</property>
<property name="ypad">0</property>
<property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
<property name="width_chars">-1</property>
<property name="single_line_mode">False</property>
<property name="angle">0</property>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">False</property>
<property name="fill">False</property>
</packing>
</child>

<child>
<widget class="GtkSpinButton" id="spinbutton1">
<property name="visible">True</property>
<property name="can_focus">True</property>
<property name="climb_rate">1</property>
<property name="digits">0</property>
<property name="numeric">False</property>
<property name="update_policy">GTK_UPDATE_ALWAYS</property>
<property name="snap_to_ticks">False</property>
<property name="wrap">False</property>
<property name="adjustment">5 1 1000000 1 10 10</property>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>

<child>
<widget class="GtkLabel" id="label11">
<property name="visible">True</property>
<property name="label" translatable="yes"></property>
<property name="use_underline">False</property>
<property name="use_markup">False</property>
<property name="justify">GTK_JUSTIFY_LEFT</property>
<property name="wrap">False</property>
<property name="selectable">False</property>
<property name="xalign">0.5</property>
<property name="yalign">0.5</property>
<property name="xpad">0</property>
<property name="ypad">0</property>
<property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
<property name="width_chars">-1</property>
<property name="single_line_mode">False</property>
<property name="angle">0</property>
</widget>
<packing>
<property name="padding">17</property>
<property name="expand">False</property>
<property name="fill">False</property>
</packing>
</child>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>

<child>
<widget class="GtkHBox" id="hbox1">
<property name="visible">True</property>
<property name="homogeneous">True</property>
<property name="spacing">0</property>

<child>
<widget class="GtkButton" id="button3">
<property name="visible">True</property>
<property name="can_focus">True</property>
<property name="label">gtk-cancel</property>
<property name="use_stock">True</property>
<property name="relief">GTK_RELIEF_NORMAL</property>
<property name="focus_on_click">True</property>
<signal name="clicked" handler="on_button3_clicked" last_modification_time="Wed, 27 Jul 2005 01:23:42 GMT"/>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>

<child>
<widget class="GtkLabel" id="label12">
<property name="visible">True</property>
<property name="label" translatable="yes"></property>
<property name="use_underline">False</property>
<property name="use_markup">False</property>
<property name="justify">GTK_JUSTIFY_LEFT</property>
<property name="wrap">False</property>
<property name="selectable">False</property>
<property name="xalign">0.5</property>
<property name="yalign">0.5</property>
<property name="xpad">0</property>
<property name="ypad">0</property>
<property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
<property name="width_chars">-1</property>
<property name="single_line_mode">False</property>
<property name="angle">0</property>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">False</property>
<property name="fill">False</property>
</packing>
</child>

<child>
<widget class="GtkButton" id="button4">
<property name="visible">True</property>
<property name="can_focus">True</property>
<property name="label">gtk-ok</property>
<property name="use_stock">True</property>
<property name="relief">GTK_RELIEF_NORMAL</property>
<property name="focus_on_click">True</property>
<signal name="clicked" handler="on_button4_clicked" last_modification_time="Wed, 27 Jul 2005 01:23:37 GMT"/>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">True</property>
<property name="fill">True</property>
</packing>
</child>
</widget>
<packing>
<property name="padding">0</property>
<property name="expand">False</property>
<property name="fill">True</property>
</packing>
</child>
</widget>
</child>
</widget>

</glade-interface>
```

---

### Post by geraldo5002 on 2005-07-29
Try this: [wpswitcher.tar.gz](http://www.geocities.com/geraldo5002/wpswitcher.tar.gz) 

I packed the files and a script to compile the beast. 

if you still get errors let me know. 

And if you do not get any errors let me know too!  :)

---

### Post by rwabel on 2005-07-29
[QUOTE=geraldo5002]Try this: [wpswitcher.tar.gz](http://www.geocities.com/geraldo5002/wpswitcher.tar.gz) 

I packed the files and a script to compile the beast. 

if you still get errors let me know. 

And if you do not get any errors let me know too!  :)[/QUOTE]

mhh I still have the same problem. First of all here is the compile output witht the 9 warnings, maybe sth is there already bad:
```
rwabel@RALPH:~/compiling/wpswitcher $ ./compile.sh

** (/usr/lib/mono/1.0/mcs.exe:29395): WARNING **: Cannot load type 'Gtk.IconSizeGType, gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'
WPSwitcher.cs(54) warning CS0219: The variable 'test' is assigned but its value is never used

** (/usr/lib/mono/1.0/mcs.exe:29395): WARNING **: Cannot load type 'Gtk.FileChooserActionGType, gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'

** (/usr/lib/mono/1.0/mcs.exe:29395): WARNING **: Cannot load type 'Gtk.ResponseTypeGType, gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'

** (/usr/lib/mono/1.0/mcs.exe:29395): WARNING **: Cannot load type 'Gtk.OrientationGType, gtk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'
TrayLib.cs(51) warning CS0219: The variable 'gdkwin' is assigned but its value is never used
TrayLib.cs(64) warning CS0219: The variable 'gdkwin' is assigned but its value is never used
TrayLib.cs(77) warning CS0219: The variable 'gdkwin' is assigned but its value is never used

** (/usr/lib/mono/1.0/mcs.exe:29395): WARNING **: Cannot load type 'Gdk.FilterReturnGType, gdk-sharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'
TrayLib.cs(15) warning CS0169: The private field 'Egg.TrayIcon.stamp' is never used
TrayLib.cs(16) warning CS0169: The private field 'Egg.TrayIcon.orientation' is never used
TrayLib.cs(19) warning CS0169: The private field 'Egg.TrayIcon.manager_atom' is never used
TrayLib.cs(21) warning CS0169: The private field 'Egg.TrayIcon.orientation_atom' is never usedTrayLib.cs(23) warning CS0169: The private field 'Egg.TrayIcon.filter' is never used
Compilation succeeded - 9 warning(s)
```

I hope we can resolve that problem.

thanks for your help

---

### Post by geraldo5002 on 2005-07-29
Fixed the script. 

mcs -pkg:gtk-sharp-2.0,gconf-sharp-2.0,glade-sharp-2.0,gnome-sharp-2.0 -resource:gui.glade WPSwitcher.cs TrayLib.cs

You can download the file pack with updated script [here](www.geocities.com/geraldo5002/wpswitcher1.tar.gz) 

Now it will work.... I hope... ](*,)

---

### Post by rwabel on 2005-07-29
[QUOTE=geraldo5002]Fixed the script. 

mcs -pkg:gtk-sharp-2.0,gconf-sharp-2.0,glade-sharp-2.0,gnome-sharp-2.0 -resource:gui.glade WPSwitcher.cs TrayLib.cs

You can download the file pack with updated script [here](www.geocities.com/geraldo5002/wpswitcher1.tar.gz) 

Now it will work.... I hope... ](*,)[/QUOTE]
 works great now! thanks
It would be cool to see the actual background as an icon/thumbnail instead of the green icon. Like wp-tray. Furthermore I think it would be better to have the interval in minutes and not seconds. 
It's really a good alternative to wp-tray

---

### Post by geraldo5002 on 2005-07-29
I'm glad it worked after all. 

I'll add some features and clean the code (it is very messy!).

Some things are not working as they should:

a) I put the program to run at the start in my "sessions", but the icon doesn't apear in the tray.
b) The pictures are not really random (some pictures appear several times and other never). I'll try to implement a better random scheme. Maybe I'll put options to display pictures randomly or in sequence.
c) There's no option to strech or tile the picture. Will work on that...

After all, considering the time I spend in the whole thing, it's working very fine on my hoary. C# it a really cool language.

---

### Post by pt123 on 2005-07-30
Got wallpaper tray 0.46 working, its really an amazing program, does everything the windows app did. Its great because it does sub directories.

---

### Post by rwabel on 2005-07-30
[QUOTE=geraldo5002]I'm glad it worked after all. 

I'll add some features and clean the code (it is very messy!).

Some things are not working as they should:

a) I put the program to run at the start in my "sessions", but the icon doesn't apear in the tray.
b) The pictures are not really random (some pictures appear several times and other never). I'll try to implement a better random scheme. Maybe I'll put options to display pictures randomly or in sequence.
c) There's no option to strech or tile the picture. Will work on that...

After all, considering the time I spend in the whole thing, it's working very fine on my hoary. C# it a really cool language.[/QUOTE]
 :-)
maybe you can take a look at wp-tray and get some help or ideas

---

### Post by pt123 on 2005-07-30
But wp_tray locks up after 10 or so changes.

---

### Post by rwabel on 2005-07-30
[QUOTE=pt123]But wp_tray locks up after 10 or so changes.[/QUOTE]
 that's not the case for me. Did you have any problems while compiling? What are the outputs in the console? Maybe we can find the source of the problem

---

### Post by pt123 on 2005-07-30
[QUOTE=rwabel]that's not the case for me. Did you have any problems while compiling? What are the outputs in the console? Maybe we can find the source of the problem[/QUOTE]
 Not that I was I aware of it seemed to compile fine. Try changing the wallpaper after a few times the icon in the task bar goes dead.

---

### Post by rwabel on 2005-07-30
[QUOTE=pt123]Not that I was I aware of it seemed to compile fine. Try changing the wallpaper after a few times the icon in the task bar goes dead.[/QUOTE]
 no, works fine for me. Did chnge the wp many times. Start it from the console and post the output. Maybe that will help us to understand why it's crashing

---

### Post by pt123 on 2005-07-30
[QUOTE=rwabel]no, works fine for me. Did chnge the wp many times. Start it from the console and post the output. Maybe that will help us to understand why it's crashing[/QUOTE]
 I started it from console it still froze, but there was no output in the console.

---

### Post by Raptor Ramjet on 2005-09-14
Have a look at:

[http://gnome-hacks.jodrell.net/hacks.html?id=6](http://gnome-hacks.jodrell.net/hacks.html?id=6)

For a quick solution (which I'm just about to try myself as it looks relatively straightforward)

---

### Post by Raptor Ramjet on 2005-09-14
Hello,

After trying this myself there's a small error in the script on line 3 (the "ALIST=(..." line)  So my script now looks like this:

#!/bin/bash
WALLPAPERS="/home/ramjet/Wallpaper" #<--- change this to your wallpapers directory
ALIST=( `ls -w1 $WALLPAPERS` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat $WALLPAPERS/.last` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

And it works a treat!  So many thanks for a top tip.

---

### Post by boysha on 2005-10-12
Hi,
I come straight from Windows world and I don't know anything about Ubuntu.
I am very amazed by it though. I can do most things that I did with W but I am far away from understanding how things work here...
Anyhow, I would like to change the brown/tan colour of my desktop and would like to learn how to do it.
Can anyone help?
Keep in mind - I am totaly new to Ubuntu/Linux but would very much like to learn and at some point get rid of W.
Thanks in advance.

Regards,
Neb

---

### Post by Vlammetje on 2005-10-22
Well I'm all new to linux as well, but getting the hang of things bit by bit.

For wallpapers it's really very easy: you rightclick your current wallpaper and pick 'change desktop background' (last option on my version) and then you get to pick one of the preloaded walls, no wall but a colour picker, or add new images as wallpaper that you can then set as wallpaper.

For changing the 'rest' of your look, you need to go through the 'themes' option (system , preferences, themes) which work, as long as you do not press 'install theme' but choose 'theme details' instead.

There are a number of themes preloaded, obviously you can get many more from the web. There are 'themes' for your general look, icon themes, splash screens, fonts and heaven knows what else... plenty to choose from ;)

---

### Post by poptones on 2005-10-22
Here's an update to the script. Thie new  while loop will make the selections more random and prevent repetition, and the last two lines will allow you to set the desktop decoration to change automatically (comment out the last two lines with a "#" if you don't want this)

```

#!/bin/bash
WALLPAPERS=~/wallpapers
ALIST=( `ls -1 $WALLPAPERS` )
RANGE=${#ALIST[@]}
lastnum=1
number=1
while [[ "$lastnum" -eq "$number" ]]; do
	let lastnum="0 + `cat $WALLPAPERS/.last`"
	let "number = $RANDOM + $lastnum"
	let "number = $number % $RANGE"
done	
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}
sleep 30 #change this to the number of seconds you want between changes
~/wallpapers/.randomwallpaper

```

---

### Post by sexcopter on 2005-10-25
Hi, I'd like to try geraldo5002's application, but I get this error:

> james@james:~$ sh ~/Desktop/wpswitcher/compile.sh
error CS2001: Source file 'WPSwitcher.cs' could not be opened
error CS2001: Source file 'TrayLib.cs' could not be opened
Compilation failed: 2 error(s), 0 warnings
james@james:~$

so am I missing some kind of compiling software? I'm not at all savvy with the Linux world ;) 
Any help much appreciated!

James.

---

### Post by papabean on 2005-10-26
[quote=poptones]Here's an update to the script.[/quote]

Thank you so much for the script.  I use Macs at work and this is one feature that I sorely missed at home.  I tried chbg, which is in the repos, but it caused Nautilus to crash every time I ran it.  This works much better.

---

### Post by kroiz on 2005-10-28
> **poptones]Here's an update to the script. Thie new  while loop will make the selections more random and prevent repetition, and the last two lines will allow you to set the desktop decoration to change automatically (comment out the last two lines with a "#" if you don't want this)

```

#!/bin/bash
WALLPAPERS=~/wallpapers
ALIST=( `ls -1 $WALLPAPERS` )
RANGE=${#ALIST[@]}
lastnum=1
number=1
while [[ "$lastnum" -eq "$number" ]] said:**
> }
sleep 30 #change this to the number of seconds you want between changes
~/wallpapers/.randomwallpaper>

```

thanks for the script poptones.
but it does not work for me.
any idea what these error mean?
```

cat: /usr/share/backgrounds/.last: No such file or directory
randomwallpaper.sh: line 8: let: lastnum=0 + : syntax error: operand expected (error token is " ")

```

should i create a file called .last?

---

### Post by sexcopter on 2005-11-01
Ok, I found out what I was doing wrong. I just needed to cd into the directory and /.compile.sh
So now it's installed, only with minor errors, and now I can't see how to invoke it. Is there a terminal command or an icon I've missed? Or do I have to do something else after compile.sh to actually install it?

---

### Post by cvmostert on 2005-11-06
[QUOTE=poptones]
Save this in a /home/username/wallpapers/ directory as ".randomwallpaper.sh" and make a panel launcher to it with this in the command:

sh /home/*username*/wallpapers/.randomwallpaper.sh
[/QUOTE]

Worked great, thanx! where can i start to learn and program scripts like this?

---

### Post by kroiz on 2005-11-06
[QUOTE=cvmostert]Worked great, thanx! [/QUOTE]

Mmm, Am I the only one that this script does not work for him.
can you please tell me what this does:
```
cat $WALLPAPERS/.last
```

this is the line from the script that fail for me.
ofcourse you need to set $WALLPAPERS.

---

### Post by poptones on 2005-11-06
.last just has the last value the randomizer chose. 

Here's an update that should no longer give that problem...

> 
#!/bin/bash
WALLPAPERS=~/wallpapers
ALIST=( `ls -1 $WALLPAPERS` )
RANGE=${#ALIST[@]}
lastnum=1
number=1
if ! [[ -f .last ]]; then echo "1" >.last; fi
while [[ "$lastnum" -eq "$number" ]]; do
	let lastnum="0 + `cat $WALLPAPERS/.last`"
	let "number = $RANDOM + $lastnum"
	let "number = $number % $RANGE"
done	
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}
sleep 30 #change this to the number of seconds you want between changes
~/wallpapers/.randomwallpaper


if you put the script in the ~/wallpapers directory as I suggest you will not have to change or define anything.

Keep in mind: you don't have to actually fill this folder up with artwork. links to artwork work just as well and they won't fill up the space on your home directory.

---

### Post by kroiz on 2005-11-06
[QUOTE=poptones].last just has the last value the randomizer chose. 

Here's an update that should no longer give that problem...

if you put the script in the ~/wallpapers directory as I suggest you will not have to change or define anything.
[/QUOTE]
thanks allot poptones.it works great now. plus I learned some bash on the way.

I used to put my wallpapers in /usr/share/backgrounds because I saw that the wallpaper that came with ubuntu reside there.
that cause another problem since /usr belongs to root. so I had to run the script as root.

[QUOTE=poptones]Keep in mind: you don't have to actually fill this folder up with artwork. links to artwork work just as well and they won't fill up the space on your home directory.[/QUOTE]

oh that is a great idea. :D I guess I still thinks as a dumb windows user.

---

### Post by evilgenius39 on 2005-11-07
I put this script in and made the launcher and all, but I can't seem to get the "sleep" function to work correctly.  The wallpaper will change when I click the launcher, but I can't get it to change after that.  I changed the sleep value to 60 just to test it, but it won't change.  Is there something I'm missing?

---

### Post by poptones on 2005-11-07
I don't know why it wouldn't run for you on a schedule. I checked it again just now and it worked fine for me. Is the file marked executable? Let's try this step by step with a brand new version that does away with the ".last" kludge...

```
#!/bin/bash
WALLPAPERS=~/wallpapers

# find the identity of the current wallpaper...
# get the name...
THISONE=`gconftool-2 -g /desktop/gnome/background/picture_filename`

# Chop off the path
THISONE=${THISONE##*/}

# locate the filename by index in this directory
THISONE=`ls -1 $WALLPAPERS | grep -n $THISONE`

# make the grep string into a valid number
THISONE=0${THISONE%%:*}

# get a directory list
ALIST=( `ls -1 $WALLPAPERS` )

# get the number of lines in that list
RANGE=${#ALIST[@]}

# programmers trick to make a 'while' loop that runs at least once...
lastnum=1
number=1

while [[ "$lastnum" -eq "$number" ]]; do
# Now randomize until we have a new number that is not the same as the old one...
	let lastnum=$THISONE
	let "number = $RANDOM + $lastnum"
	let "number = $number % $RANGE"
done

# Set wallpaper to selection indexed by new "number"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

# Uncomment next two lines if you want to make a wallpaper switcher you can set your clock by,..
#sleep 10 #change this to the number of seconds you want between changes
#$WALLPAPERS/.randomwallpaper

```

Copy the text above to a file called ".randomwallpaper" in a folder called "wallpapers" in your home folder. Open the folder in nautilus, select "show hidden files" and then right click the file and select "properties." In the permissions tab set the file to "executable" by clicking the top right checkbox.

Now make a custom launcher for your panel and tell it to run this file by setting "command" to /home/**yourlogin**/wallpapers/.randomwallpaper

Launch the applet once by clicking on the launcher. If you uncommented the last two lines by removing the first # then it will continue to run every x number of seconds (where x is the number after "sleep")

---

### Post by evilgenius39 on 2005-11-07
Rock on man, now it works.  Thanks for the step-by-step too.  Might be able to learn some from this too.

---

### Post by sexcopter on 2005-11-08
Hey, poptones, you are a legend... your script works fine for me (only had to chage the path to my wallpapers folder)

I found putting it in the startup list under System->Preferences->Sessions worked fine to make it change wallpaper on log-in.

I only have one slight (but not crucial) grumble. If I click on the launcher several times (maybe on one day I don't want a particular wallpaper...) or log out and back in, I inevitably get multiple instances of .randomwallpaper and sleep. Is there a way for the script to first of all killall any instances of these processes in order to keep the list of processes clean and also so it only changes wallpaper when it should?

Otherwise, a masterpiece if I ever saw one! Cheers man.

James.

*edit* Actually I've just realised, multiple instances accumulate in any case, even if I only run it once, so things could get rather messy if it's left for a long time...

---

### Post by poptones on 2005-11-09
Right you are... to duplicate it I set the time interval to ten seconds, clicked the launcher a few times and the load almost brought down my desktop! And a stupid mistake, too... so let's fix it.

REMOVE the last three lines.
```

# Uncomment next two lines if you want to make a wallpaper switcher you can set your clock by,..
#sleep 10 #change this to the number of seconds you want between changes
#$WALLPAPERS/.randomwallpaper

```

Get rid of'em... now, schedule it properly using the system tools.

crontab is a file that you can look at as your own personal alarm clock. It doesn't require a gui and it's pretty easy to set. Here's a quick tutorial.

[http://www.clockwatchers.com/cron_general.html](http://www.clockwatchers.com/cron_general.html)

One important thing to keep in mind is that * means "every" just like with files. So if you set something to "4" it won't do it every 4 (minutes, hours, days) but instead will do it every day at four, or every hour at four minutes past... get it?

So to make something happen "every fifteen minutes" what do we do? We divide "all" into 15 minute blocks...

*/4 * 0 0 0 /runthis/task

Means "divide minutes by four" which happens to equal 15. 

*/6 * 0 0 0 /runthis/task

Means "every ten minutes..."

No, this isn't gee whiz with all that gui stuff, but the point here is that linux has pretty much **everything you need** already, you only need to learn how to use it to do what you want. Sleep timer for tvtime? Morning alarm clock? Just set the task you want and let fly...

*Teach a man to fish...*

---

### Post by sexcopter on 2005-11-10
Ok, thanks for that poptones. I've never understood what cron(tab) is/does, so I'm learning as I go :)
As it happens, doing */2 * * * * for every 30 minutes didn't seem to work, but 0,30 * * * * did, which does virtually the same thing.

---

### Post by Noelinho on 2005-12-01
I tried to add the wallpaper changer to the panel:

right click on the top launcher panel --> add to panel --> custom luancher application --> gave it a name, and put in the command 'sh /home/username/wallpapers/.randomwallpaper.sh', type 'application', added an icon.

When I click on the icon, it does nothing. :( Have I done something wrong?

EDIT: I'm an idiot, helps if I change 'username' to 'noel'!

---

### Post by Noelinho on 2005-12-01
[QUOTE=poptones]Copy the text above to a file called ".randomwallpaper" in a folder called "wallpapers" in your home folder. Open the folder in nautilus, select "show hidden files" and then right click the file and select "properties." In the permissions tab set the file to "executable" by clicking the top right checkbox.[/QUOTE]

I can't see the file. When I go to preferences --> view hidden files, they don't show up.

---

### Post by Marller on 2005-12-10
[QUOTE=Noelinho]I can't see the file. When I go to preferences --> view hidden files, they don't show up.[/QUOTE]


Don't worry, the file does not exist, if you never created it. :)
You create the file with the code he posted. Just save it under ".randomwallpaper" with your text editor and set the permissions as he said.

---

### Post by Cordate on 2005-12-16
Poptone's script mostly worked for me, but it doesn't like filenames with spaces in them, like "pretty sunset.jpg" 

I tried to make a script that would make symlinks to my images, place them in a different folder and then rename the links with basic filnames, but for some reason it was creating broken links. I'll have to try messing around with it sometime and see if I can find what's going on.

But I *also* found this python script in [this thread]('http://www.ubuntuforums.org/showthread.php?t=18163&highlight=wallpaper+script') that seems to be able to handle all my images. (*hurrah!*) It also can use multiple directories, which is nice. Check it out!

---

### Post by [pl]ice on 2006-02-08
[QUOTE=poptones]OK, I'll mess with it a bit and repost. So long as *someone* finds value in it I won't feel like I'm wasting my time...[/QUOTE]
hey man, have u tried changing that script? pitty i can't program using cli :(
i get the following error caming up often :
./bcg: line 29: let: lastnum=048: value too great for base (error token is "048")

no idea ;) 
thnx for help :)

---

### Post by [pl]ice on 2006-02-08
[QUOTE=poptones]OK, I'll mess with it a bit and repost. So long as *someone* finds value in it I won't feel like I'm wasting my time...[/QUOTE]

hey man, have u tried changing that script? pitty i can't program using cli :(
i get the following error caming up often :
./bcg: line 29: let: lastnum=048: value too great for base (error token is "048")

no idea ;) 
thnx for help :)

---

### Post by anil_robo on 2006-03-06
wp_tray version 0.4.6-3 does not work well in Dapper. It installs fine, even sits in tray when run. But I try to add some directories containing wallpapers to its preferences using GUI right click - can't do a thing there. No error - nothing happens at all! Wish someone could make a debian package of Geraldo's script and add it to the official Ubuntu repositories. I won't miss Webshots so much then!

---

### Post by Teleyinex on 2006-03-09
Well, I have found this thread today, but I think that this little app could be usefull. I had been searching for an application that change the wallpaper, but I dont find nothing that works well, (like I wanted). I decided to write one. The application is here:
[http://www.gnomefiles.org/app.php?soft_id=938](http://www.gnomefiles.org/app.php?soft_id=938)

There are two scripts. One for change randomly from your Wallpaper folder. You must have the backgrounds in there.

Second one is the best ;). The second one creates a list of all wallpapers that are in art.gnome.org. Then, you can specify your screen resolution in the screen, so you only download the ones that fits your screen or are less in resolution. Then each day you boot up your computer you will have a new wallpaper. Best of this, is that you will never have the same wallpaper, for a long long time, because art.gnome.org will always have new wallpapers.

Cya!

---

### Post by chadk on 2006-05-16
Love it.

---

### Post by llebegue on 2006-05-30
I made my own script based upon poptones' one 

EDIT: changed the recusrsive call for a while loop ... better

```

#!/bin/bash

while [ 1 == 1 ]
do
ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g' | grep $HOME` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat .ludolastwallpaper` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > .ludolastwallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}

sleep 300
done

```

The main difference is that it works from the 'gnome-background-properties' application configuration.
The key line of code is this one :
```

ALIST=( `grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g'` )

```

---

### Post by digitalchef on 2006-07-05
here is  another link for [COLOR="Red"]wp-tray [/COLOR] 
[http://wildbill.nulldevice.net/ubuntu/wp_tray_0.4.6-1_i386.deb]("http://wildbill.nulldevice.net/ubuntu/wp-tray_0.4.6-1_i386.deb")
  
I hope we all konw how to install packages that we've already downloaded 
 
The only problem im haveing with is i cant seem to get different wallpaper into it. the files i choose wont work . and if i put the folder there in it crashes soooooo. if you get 
it  and figure it out , start a how to thread or something.

Oh yeah so i stay out of trouble i got that link from Ubuntu Hacks

---

### Post by ShiftyPowers on 2006-07-09
by the way, this poptones script is awesome.  I used to use one called change-bg but it didn't change amongst my entire list, only a few wallpapers for some reason.  

I put this script in the Startup Sessions options as opposed to a panel launcher so that it automagically runs when I log in.

---

### Post by eternalsword on 2006-07-19
[thanks to llebegue and poptones]

here's a script that reads the gnome backgrounds.xml file, but this one can read spaces.  I didn't do random, I just go through one by one, which exhausts the entire list before seeing an old one, unlike random which can display the same ones multiple times.  The script also saves a current list of all wallpapers. I use a cron file rather than sleep

```

#!/bin/bash
IFS=$'\n'
grep filename ~/.gnome2/backgrounds.xml | sed 's/<filename>//g' | sed 's/<\/filename>//g' | sed 's/^[ \t]*//;s/[ \t]*$//' > .wallpaperlist
ALIST=( `cat .wallpaperlist` )
RANGE=${#ALIST[@]}
let LASTNUM="`cat .lastwallpaper` + 1"
let "number = $LASTNUM % $RANGE"
echo $number > .lastwallpaper
echo "${ALIST[number]}" > .currentwallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename ${ALIST[$number]}

```

copy the code and save the file to ~/wallpaper/.wallpaper
then run this from the terminal

chmod +x ~/wallpaper/.wallpaper
echo "0" > ~/wallpaper/.lastwallpaper

then you should be ready to go.

to get the script to run every hour, you can do this
(make sure to replace [yourusername] appropriately

mkdir ~/.cronfiles
echo "01 * * * * /home/[yourusername]/wallpaper/.wallpaper" > ~/.cronfiles/cronfile
crontab /home/[yourusername]/.cronfiles/cronfile

you can also add 
crontab /home/[yourusername]/.cronfiles/cronfile
to your start up commands

to add wallpapers, just use System -> Preferences -> Desktop Background

---

### Post by true_friend on 2006-08-15
nice.
if i want to change my wallpaper after 15 minutes.
how it would work????????
i think it cannot be run by adding in startup. as it is using cron which is also a scheduling tool (some thing same kind as i understand).
is it not possible to add a custom folder???? instead of using befault background folder.

---

### Post by eternalsword on 2006-08-16
if you want to use a custom folder, here's another script

```

#!/bin/bash
IFS=$'\n'
ls "/media/sda3/Shared Documents/My Pictures" | sed 's/^[ \t]*//;s/[ \t]*$//' > .wallpaperlist
ALIST=( `cat .wallpaperlist` )
RANGE=${#ALIST[@]}
let LASTNUM="`cat .lastwallpaper` + 1"
let "number = $LASTNUM % $RANGE"
echo $number > .lastwallpaper
echo "${ALIST[number]}" > .currentwallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/media/sda3/Shared Documents/My Pictures/${ALIST[$number]}"

```

just change the folders in line three and the last line.  when running as a cron task, .wallpaperlist .lastwallpaper and .currentwallpaper will be in your home directory  if running manually, it will be in the same directory as the script file.

---

### Post by eternalsword on 2006-08-17
this one improves on both scripts. you need to create a .directorylist file and put it into the .wallpaper folder in your home directory
the .directorylist file contains one path on each line to folders you want to use.

my .directorylist file
```

/media/sda3/Shared Documents/My Pictures/

```
it can have however many entries that you want.

```

#!/bin/bash
IFS=$'\n'
ALIST=( `cat ~/.wallpaper/.directorylist` )
COUNTER=${#ALIST[@]}
find "${ALIST[$COUNTER-1]}" -maxdepth 1 -mindepth 1 -type f | grep ".jpg\|.png" > .wallpaperlist
let COUNTER-=1
until [  $COUNTER -lt 1 ]; do
find "${ALIST[$COUNTER-1]}" -maxdepth 1 -mindepth 1 -type f | grep ".jpg\|.png" >> .wallpaperlist
let COUNTER-=1
done
#ls "/media/sda3/Shared Documents/My Pictures" | sed 's/^[ \t]*//;s/[ \t]*$//' > .wallpaperlist
ALIST=( `cat .wallpaperlist` )
RANGE=${#ALIST[@]}
let LASTNUM="`cat .lastwallpaper` + 1"
let "number = $LASTNUM % $RANGE"
echo $number > .lastwallpaper
echo "${ALIST[number]}" > .currentwallpaper
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "${ALIST[$number]}"

```

---

### Post by RajivNair on 2006-08-19
People check this out:-

[http://www.gnomefiles.org/app.php/Desktop_Drapes](http://www.gnomefiles.org/app.php/Desktop_Drapes)

---

### Post by pt123 on 2006-08-19
That is a neat program. Lot of the features I have been looking for since I started this thread. I wish there was a mass add for whole directories.

---

### Post by eternalsword on 2006-08-19
> **pt123 said:**
> That is a neat program. Lot of the features I have been looking for since I started this thread. I wish there was a mass add for whole directories.

One of these days I'll write a c program that will have that functionality and it will be true random rather than the sequential that my bash script is doing right now.  Are there any other features that you think would be useful?

---

### Post by true_friend on 2006-08-21
yum yum. a lot of softwares again. this new software, could it be installed by me???????? :(( 
i always struggled in gnome for background changing. ok try it and before it a ton of dependencies that are requiered by it. nano it means it is written in .net??? i heared nano is a project to run .net applications of linux. ok i search it in synaptic if it is avaialble.
and eternalsword u are a nice man buddy. tried ur best to help me. what a rubbish i have all ok but can not run script 15 minutes. huh struggling for correct cron job entry.
but hope ur software or Desktop _Dapes may help me.
eternalsword: why u do not take weshots desktop as a model???
or some of its featrues including a custom folder, a realiy realiy random effect, ability to change at any time, no sudo or root problems, run may be in background or may in system tray.
there is a software chbg. u can see it on sourceforge. it is installed running very well but not too easy to be configured. foolish setup it does not remember the folder to pick pictures. u have to manually add every time u start it. huh.
and i was forgetting to add some wallpapers from some custom websites like webshots comunity website, gnome art etc..
so a lot of wishes and waiting for an ideal wallpaper changer for gnome which can be installed easily and run also easily and and can change wallpaper according to desires.
i give my out put about Desktop_Drapes how it worked for me.
thnx a lot all of u friends. hoping for a good utility for gnome DE.
Regards 
True_Friend

---

### Post by true_friend on 2006-08-21
first feed back for RajivNair's software. its debian installer crashes at file number 16 downloading. i can not say why but it just disappears.
plz see this buddy.
Regards
True_Friend

---

### Post by czer323 on 2006-10-10
Draper was an awesome look'n program.  I'm having some issues with picture thumbnails myself at the moment, but I think it's related to nautilus being buggy on Edgy.  Other than that, the interface looks pretty clean.  I"m pretty excited to use it.

---

### Post by czer323 on 2006-10-10
After using Drapes for a bit, I'm blown away.  Great program.  Still in beta in my opinion, but MUCH better than trying to string together a script in my opinion.  It's something that I could put on my sister's installation of Ubuntu, and she could use.

---

### Post by jsandys on 2006-10-19
The code by poptone in message 5 worked great for me.  I added it to the startup so I get a new background every time I started up.

But then I thought instead of duplicating my pictures from my_pictures folder and my_wallpapers folder, I would just put links in my_wallpapers folder.  The problem is that when you make a link with Nautilus the filename of the link is "link to filename", **with spaces**.  The change background script breaks with a message about can't find the file "to".

Is there a way to change the behavior of Nautlilus, to make more unix suitable filenames for links?  See my thread:
[http://ubuntuforums.org/showthread.php?t=280353](http://ubuntuforums.org/showthread.php?t=280353)

Thanks,
Jeff Sandys

---

### Post by CatKiller on 2006-10-19
You can do it from the command line: cd to the directory that you'd like the link and type ```
ln -s */path/to/linkee*
``` This will make a link whose name is the same as the linkee. You can stick a name you'd prefer at the end to get a different name for the link.

---

### Post by eternalsword on 2006-10-21
> **jsandys said:**
> The code by poptone in message 5 worked great for me.  I added it to the startup so I get a new background every time I started up.

But then I thought instead of duplicating my pictures from my_pictures folder and my_wallpapers folder, I would just put links in my_wallpapers folder.  The problem is that when you make a link with Nautilus the filename of the link is "link to filename", **with spaces**.  The change background script breaks with a message about can't find the file "to".

Is there a way to change the behavior of Nautlilus, to make more unix suitable filenames for links?  See my thread:
[http://ubuntuforums.org/showthread.php?t=280353](http://ubuntuforums.org/showthread.php?t=280353)

Thanks,
Jeff Sandys

linux handles spaces just fine.  script writers usually forget to take it into account which results in input being cut off at every space

the script I wrote at
[http://www.ubuntuforums.org/showpost.php?p=1388559&postcount=81](http://www.ubuntuforums.org/showpost.php?p=1388559&postcount=81)
[http://www.ubuntuforums.org/showpost.php?p=1388559&postcount=83](http://www.ubuntuforums.org/showpost.php?p=1388559&postcount=83)
[http://www.ubuntuforums.org/showpost.php?p=1388559&postcount=84](http://www.ubuntuforums.org/showpost.php?p=1388559&postcount=84)

all handle spaces in file paths and names.  the first uses the images already added as backgrounds.  The second utilizes one folder written into the script.  The third utilizes an external file (which the user must create/maintain) with a list of directories to look in for wallpapers

---

### Post by jsandys on 2006-10-23
> **eternalsword said:**
> linux handles spaces just fine.  script writers usually forget to take it into account which results in input being cut off at every space...

The scripts you wrote have quotes around the filename in the gconftool-2 line.  Is that what is missing in this line from poptones post, the 5th post of this thread?
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}

```should be```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$WALLPAPERS/${ALIST[$number]}"
```?

the reply I got from eternalsword is:
[INDENT]no, the part that's usually missing is the
IFS=$'\n'

usually spaces from input cause a line break. the IFS=$'\n' tells the script to only break at a line break.[/INDENT]

---

### Post by phenest on 2007-04-28
I'm new to scripts. I can't get it to work. Here's the problem:

(This is using the original script posted by poptones)

.wallpaperchanger.sh: 3: Syntax error: "(" unexpected
 So I deleted the "(" and ")" to see what happens:

.wallpaperchanger.sh: 5: let: not found
cat: ~/wallpapers/.last: No such file or directory
.wallpaperchanger.sh: 6: let: not found
.wallpaperchanger.sh: 7: let: not found
.wallpaperchanger.sh: 8: cannot create ~/wallpapers/.last: Directory nonexistent
.wallpaperchanger.sh: 9: Syntax error: Bad substitution

Erm, I have no idea what to do next.

---

### Post by ramasdf123 on 2007-05-04
so, i got this wallpaper changer working but the thing that really bugs me is that the default settings make it 'fit' the screen, but i want it to fill the screen whenever a wallpaper changes,  I have different sizes of images so i want to use them all without making it fill screen by my self.

I would also like to clear the recently used wallaper list on restart?

any ways to fix these problems?

---

### Post by Jdratcliffe on 2007-05-04
> **geraldo5002 said:**
> I changed the script a bit, putting a "find" instead of "ls" to generate the ALIST.

But spaces in filenames are a problem... :-(

So i did a little app using mono to change the wallpaper. It's a small console app, but works. I'm gonna create now a small GUI to set the base dir options. Is working fine in my system...

Then I'll try to find some place to put the file for those who want to try it...

i would be interested

---

### Post by pt123 on 2007-06-10
Here is a link to another thread on switching wallpaper randomly that me and others have worked on.

The last version does sub directories.

[http://ubuntuforums.org/showthread.php?t=329164&page=3](http://ubuntuforums.org/showthread.php?t=329164&page=3)

---

### Post by Palmyra on 2007-11-25
I didn't go through all the pages, but try using wallpaper-tray.  It randomly changes wallpapers at chosen intervals (you set the minutes), and it also changes the wallpaper at logon, if you like.  

It suits my needs.  Hopefully it will be integrated into Gnome.

---

