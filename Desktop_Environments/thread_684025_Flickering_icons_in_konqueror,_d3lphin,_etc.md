---
title: "Flickering icons in konqueror, d3lphin, etc"
date: 2008-01-31
forum: Desktop Environments
---

### Post by thefirstM on 2008-01-31
I am using Kubuntu 7.10 with KDE 3.5.8.  Often, when I mouse over an icon in Konqueror or Dolphin, it will flicker.  Also, this occurs with the toolbar buttons in OpenOffice, and sometimes occurs with the side icons in the K menu.  I have done some research and found out that the problem occurs because the icon is redrawn to the front buffer, instead of double-buffering the redraw.  I have also found a patch to fix this, but I have no idea how to use it.  I was wondering if maybe there was a developer out there who could apply this patch to Qt in the Unsupported updates repository, or tell me how I could apply it to my system.  Here is a link to the page with the patch [http://robotics.dei.unipd.it/~koral/KDE/kflicker.html]("http://robotics.dei.unipd.it/~koral/KDE/kflicker.html").
And here is the patch:

```
Buffered QIconView.

For every QIconView this patch creates a backbuffer where the image will
grow up (aka will be painted) before blitting the results to the screen.
This solves the konqueror flickering problems at its roots. There are
some more bugs that make conqueror repaint without reason.. patches
will follow.
 Enrico Ros <eros.kde@email.it>

--- src.orig/iconview/qiconview.cpp	2004-03-24 15:58:05.000000000 +0000
+++ src/iconview/qiconview.cpp	2004-03-30 16:23:32.521253280 +0000
@@ -211,6 +211,7 @@
     QIconViewItem *currentItem, *tmpCurrentItem, *highlightedItem,
 	*startDragItem, *pressedItem, *selectAnchor, *renamingItem;
     QRect *rubber;
+    QPixmap *backBuffer;
     QTimer *scrollTimer, *adjustTimer, *updateTimer, *inputTimer,
 	*fullRedrawTimer;
     int rastX, rastY, spacing;
@@ -2731,6 +2732,7 @@
     d->currentItem = 0;
     d->highlightedItem = 0;
     d->rubber = 0;
+    d->backBuffer = 0;
     d->scrollTimer = 0;
     d->startDragItem = 0;
     d->tmpCurrentItem = 0;
@@ -2883,6 +2885,8 @@
 	delete item;
 	item = tmp;
     }
+    delete d->backBuffer;
+    d->backBuffer = 0;
     delete d->fm;
     d->fm = 0;
 #ifndef QT_NO_TOOLTIP
@@ -4845,6 +4849,47 @@
 #endif
 
 /*!
+    This function grabs all paintevents that otherwise would have been
+    processed by the QScrollView::viewportPaintEvent(). Here we use a
+    doublebuffer to reduce 'on-paint' flickering on QIconView
+    (and of course its childs).
+    
+    \sa QScrollView::viewportPaintEvent(), QIconView::drawContents()
+*/
+
+void QIconView::bufferedPaintEvent( QPaintEvent* pe )
+{
+    QWidget* vp = viewport();
+    QRect r = pe->rect() & vp->rect();
+    int ex = r.x() + contentsX();
+    int ey = r.y() + contentsY();
+    int ew = r.width();
+    int eh = r.height();
+
+    if ( !d->backBuffer )
+	d->backBuffer = new QPixmap(vp->size());
+    if ( d->backBuffer->size() != vp->size() ) {
+	//Resize function (with hysteesis). Uses a good compromise between memory
+	//consumption and speed (number) of resizes.
+	float newWidth = (float)vp->width();
+	float newHeight = (float)vp->height();
+	if ( newWidth > d->backBuffer->width() || newHeight > d->backBuffer->height() )
+	{
+	    newWidth *= 1.1892;
+	    newHeight *= 1.1892;
+	    d->backBuffer->resize( (int)newWidth, (int)newHeight );
+	} else if ( 1.5*newWidth < d->backBuffer->width() || 1.5*newHeight < d->backBuffer->height() )
+	    d->backBuffer->resize( (int)newWidth, (int)newHeight );
+    }
+
+    QPainter p;
+    p.begin(d->backBuffer, vp);
+    drawContentsOffset(&p, contentsX(), contentsY(), ex, ey, ew, eh);
+    p.end();
+    bitBlt(vp, r.x(), r.y(), d->backBuffer, r.x(), r.y(), ew, eh);
+}
+
+/*!
     \reimp
 */
 
@@ -5627,7 +5676,7 @@
 		    if ( !d->rubber )
 			drawDragShapes( d->oldDragPos );
 		}
-		viewportPaintEvent( (QPaintEvent*)e );
+		bufferedPaintEvent( (QPaintEvent*)e );
 		if ( d->dragging ) {
 		    if ( !d->rubber )
 			drawDragShapes( d->oldDragPos );
--- src.orig/iconview/qiconview.h	2004-03-30 16:00:47.605751976 +0000
+++ src/iconview/qiconview.h	2003-05-16 13:02:38.000000000 +0000
@@ -445,6 +445,7 @@
     void contentsDropEvent( QDropEvent *e );
 #endif
 
+    void bufferedPaintEvent( QPaintEvent* );
     void resizeEvent( QResizeEvent* e );
     void keyPressEvent( QKeyEvent *e );
     void focusInEvent( QFocusEvent *e );

```

---

### Post by thefirstM on 2008-02-03
Bump

---

### Post by pelle.k on 2008-02-29
Ask, and you shall recieve! :)

That joke aside, i will tell you how i did it, in case you want to try it yourself (or maybe someone else wants to).
I will also attach the patched qt in a nice .deb for your  convenience. (you'll have to wait until i have my download repository up and running. 1-24 hours)

first i made a directory, and in that directory i ran
```
apt-get source libqt3-mt
```
and from that i got
[LIST]
[*]qt-x11-free_3.3.8really3.3.7-0ubuntu11.1.dsc
[*]qt-x11-free_3.3.8really3.3.7-0ubuntu11.1.diff.gz 
[*]qt-x11-free_3.3.8really3.3.7.orig.tar.gz
[/LIST]
then i unpacked the *debianized* source using the "debian source control" file
```
dpkg-source -x qt-x11-free_3.3.8really3.3.7-0ubuntu11.1.dsc
```
You *need* "devscripts" installed to do that.
i cd:d to the new source dir (qt-x11-free_3.3.8really3.3.7) and in to debian/patches and copied the "debianized patch" 99_flickerfree_qiconview.dpatch (attached in this post as well) there and finally added
```
99_flickerfree_qiconview
```
to the file 00list text file. The patch was converted (still, i had to edit/adjust the path to the source in the patch though) using this guide; [http://matrixhasu.altervista.org/index.php?view=use_dpatch](http://matrixhasu.altervista.org/index.php?view=use_dpatch)
Then i cd:d back to the dir i created at first and run
```
dpkg-source -b qt-x11-free_3.3.8really3.3.7
```
to build the new .diff .dsc etcetera. i did this *without* bumping version numbers in the changelog though, because it is important that new security updates from kubuntu *will* overwrite this version. So I/you/someone would have to create a new .deb in case that would happen.
Now to build a .deb i used pbuilder.
```
sudo pbuilder build qt-x11-free_3.3.8really3.3.7-0ubuntu11.1.dsc
```
A nice guide to set up a pbuilder system is; [http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382)
You *might* get away with only installing "pbuilder" and running that command, but you would still have to initialize/create it first (sudo pbuilder create).

The actual .deb (gutsy); [http://download.tuxfamily.org/pandora/temp/libqt3-mt_3.3.8really3.3.7-0ubuntu11.1_i386.deb](http://download.tuxfamily.org/pandora/temp/libqt3-mt_3.3.8really3.3.7-0ubuntu11.1_i386.deb)

---

### Post by thefirstM on 2008-02-29
Thank you SO MUCH!!!!  That flickering was really getting on my nerves, but now it is completely gone!  Now if I could just stop the flickering in Openoffice.org....

---

### Post by doublepow on 2008-03-06
That was awesome of you to package the patch as a .deb. Made things so much simpler.

I really hope this patch is carried out by ubuntu/kubuntu's automatic update functionality for others to maintain this distribution's status as a really easy to use and supported distribution.

---

### Post by thefirstM on 2008-03-06
I hope this gets included into the apt repository...  If anyone knows the people who control such things, please contact them about this and see if we can get this included.  It works very well, and has completely stopped the flickering on the 3 kubuntu systems I use.  It would be great if everyone could have it...

---

### Post by thefirstM on 2008-03-26
Just an update, I will be getting a brand new laptop with an Intel Core 2 Duo in a week, so then I will build a 64-bit .deb and post it on this thread.  I am still planning on building it for (and using) Gutsy, but I may build one for Hardy as well.

---

### Post by pelle.k on 2008-03-26
I already built one for 32 bit hardy :)
[http://ubuntuforums.org/showthread.php?t=735303](http://ubuntuforums.org/showthread.php?t=735303)

---

