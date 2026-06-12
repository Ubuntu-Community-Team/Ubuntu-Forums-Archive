---
title: "Gome 3 - Missing or Blank Application Icons"
date: 2013-12-18
forum: Desktop Environments
---

### Post by tgilber1 on 2013-12-18
Searched for web and forums for solutions to missing or blank application icons under gnome 3 environment.  Due to multiple issues, I could not find a post that addressed all issues.  Therefore, I posting some suggestions to fixing issues with application icons.

Helpful information before troubleshooting

1. Read [http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/](http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/) ##typical locations for desktop spec files are /usr/share/application or .local/share/applications

2. Read [http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) ##understand the search pattern for icons
   a.  Here's an excerpt from the icon-theme file "Icons and themes are looked for in a set of directories. By default, apps should look in $HOME/.icons (for backwards compatibility), in $XDG_DATA_DIRS/icons and in /usr/share/pixmaps (in that order).  

3. Download gthumb ## make sure that image size is symmetrical and are placed in associated folder, i.e., 64x64 should be in 64x64 folder

4.  What I mean by blank application icon on desktop or viewing applications, meaning there is an image, but it does not contains an actual image.  However, you can click on it to run application

5.  I know of four reasons for missing or blank icons
     a. image icon is missing (e.g. not installed, deleted, or soft link pointed to wrong file)
     b. Duplicate icons for same application ##personally did not run into, but have seen discussed on forums
     c. Desktop file configuration points to wrong icon file or filename
     d. image file size is not symmetical (e.g. 64x64) for size directory in the /usr/share/icons/hicolor ## use gthumb to convert to symmetrical size and place in correct directory (64x64 spotify-client.png file would go into hicolor/apps/spotify-client.png

6.  If there a theme has not been selected, then gnome3 will always default to the hicolor theme and search all subdirectories of /usr/share/icons/hicolor/ per freedesktop specification, i.e., /usr/share/icons/hicolor/apps/64x64

How to troubleshoot missing or blank image

1.  Make sure a desktop file exist for application in the /usr/share/applications directory (e..g, spotify.desktop)
2.  View desktop file and verify there is an [Icon] (e.g., Icon=spotify-client)
3.  Search for png/svg files in the /usr/share/icons, .icons, /usr/share/pixmap ## note some desktop files will provide absolute path of icon
4.  If exist, then use gthumb to view image file, making sure that file is an actual image file.  Also make sure it correct size (e.g., 64x64) with gthumb.  If not, then convert with gthumb.
5.  After making edits of any sort to image file, desktop, or installation, create a new icon.theme using the command below.  Understand, run the command on the folder of the theme you're using.  Worst case, remove all icons of the problematic application

"sudo gtk-update-icon-cache /usr/share/icons/hicolor/icon-theme.cache"

6.  Worst case, remove all icons of the problematic application and add a single image icon into any of the apps folder of any subdirectories (e.g., /usr/share/icons/hicolor/<size>/apps.  Make sure icon png or svg file exist.  Other type image files may work, but refer to freedesktop specifications for exact details.


Although not exhaustive, I hope it helps out someone having the same blank icon issue.

---

