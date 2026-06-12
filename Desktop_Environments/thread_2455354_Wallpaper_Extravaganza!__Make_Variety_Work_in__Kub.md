---
title: "Wallpaper Extravaganza!  Make Variety Work in  Kubuntu"
date: 2020-12-17
forum: Desktop Environments
---

### Post by Shibblet on 2020-12-17
Download Variety from the Software Repo.

Run Variety for the first time to initialize it.  Then immediately close Variety from the system tray.

Go into ~/.config/variety

Open up **variety.conf** in Kate (or any text editor you prefer.)
Remember anywhere I indicate ***username***, that is your user name!

Look for section that says:
```
# download_folder = <some folder> - when not specified, the default is /home/***username***/.config/variety/Downloaded
download_folder = **/home/[B]*username***/.config/variety/Downloaded[/B]
```
Change the directory to:
```
# download_folder = <some folder> - when not specified, the default is ~/.config/variety/Downloaded
download_folder = **~/Pictures/Variety**
```
This will make a "Variety" folder in your "Pictures" directory on your /home drive.  By changing this directory, you will allow KDE's Wallpaper to be able to see where the downloaded pictures are being stored.  If you make a directory starting with a .  it will be hidden, and KDE's Wallpaper program cannot see it.  i.e.  ~/.config/variety/Downloaded (notice the "dot" before config)

Now, restart Variety and open the preferences page. 
[LIST]
[*]Start Variety when the computer starts. - On
[*]Change wallpaper every (15) minutes.  - On
This can be any number.  For KDE, this setting is not how often your wallpaper will change, this setting is how often new wallpapers will download.  So, set it according to that.
[*]Change wallpaper on start - Off
***[COLOR="#FF0000"]You must turn this off!  It will cause problems with KDE's Wallpaper program.  It will keep reverting to it's default settings, and not your slideshow.[/COLOR]***
[/LIST]

Images:
[LIST]
[*]Select whichever libraries you prefer.
[*]If you choose "Favorites and Fetched" you must follow the directions below and change their directories.  I personally do not use them.
[*]Favorites:  Change the directory to **/Pictures/Variety/Favorites**
[*]
[/LIST]

You can choose anything you like on the Effects Tab.

Manual Downloading: Change the Fetch Folder to **/Pictures/Variety/Fetched**

On the Color and Size, and Customize Tabs you can select what you wish to accommodate your personal preferences.

Now that we have Variety all figured out.  Open up "Configure Desktop" and click on "Wallpaper."  The easiest way to do this is to right click on the wallpaper, and then click on "Configure Desktop."

Select:
[LIST]
[*]Layout - Folder View
[*]Wallpaper Type - Slideshow
[*]Positioning (Whatever you like, I use Scaled and Cropped)
[*]Order (Again, your preference.  I use Random)
[*]Change Every - Hour, Minute, Second (Set this for how often do you want the wallpaper to change.  I do 30 minutes.)
[*]Folders:  Delete the folders in the little window by clicking on the - sign next to the folder name.  Once the window is cleared out, we are going to add one new directory.
[*]Click on + Add Folder below, and add /home/***username***/Pictures/Variety
[/LIST]
You should watch the Wallpaper Window populate with all of the wallpapers that Variety has downloaded to your /Pictures/Variety folder.
And you desktop wallpaper should start changing to your selected intervals.

If you start to have repeating wallpapers...
[LIST]
[*]Close Variety in the system tray.
[*]go into /Pictures and delete the /Variety directory
[*]Open Variety, and watch it repopulate with new pictures!
[/LIST]

Hope this works for all of you KDE users out there!

---

### Post by ActionParsnip on 2020-12-18
Nice guide. Very clear

---

