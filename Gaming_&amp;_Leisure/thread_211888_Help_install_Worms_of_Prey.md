---
title: "Help install Worms of Prey"
date: 2006-07-09
forum: Gaming &amp; Leisure
---

### Post by hansoffate on 2006-07-09
The only instructions on the website is to use make.  

[http://wormsofprey.org/download.html](http://wormsofprey.org/download.html)

I have dpkg the src and data.  When I try to make, I get a whole bunch of errors.  Any ideas?

Thanks
-Hans

```

hansoffate@hansoffate-desktop:~/Desktop$ tar xvjf wop-0.4.3-src.tar.bz2
hansoffate@hansoffate-desktop:~/Desktop$ tar xvjf wopdata-2005-12-21.tar.bz2
hansoffate@hansoffate-desktop:~/Desktop$ cd wop-0.4.3
hansoffate@hansoffate-desktop:~/Desktop/wop-0.4.3$ make
cd sdlwidgets; make
make[1]: Entering directory `/home/hansoffate/Desktop/wop-0.4.3/sdlwidgets'
Makefile:43: Makefile.depend: No such file or directory
makedepend -f Makefile.depend -Y --  -- backgroundwidget.cpp borderwidget.cpp button.cpp focusmanager.cpp fontfactory.cpp graphics.cpp image.cpp layout.cpp rootcontainer.cpp textarea.cpp textfield.cpp textlabel.cpp widget.cpp >/dev/null 2>&1
make[1]: Leaving directory `/home/hansoffate/Desktop/wop-0.4.3/sdlwidgets'
make[1]: sdl-config: Command not found
make[1]: Entering directory `/home/hansoffate/Desktop/wop-0.4.3/sdlwidgets'
g++ -Wall -Wshadow -Wsign-compare -Wparentheses -Wconversion -g -O3 -ansi  -c backgroundwidget.cpp -o backgroundwidget.o
In file included from backgroundwidget.h:24,
                 from backgroundwidget.cpp:21:
widget.h:26:17: error: SDL.h: No such file or directory
backgroundwidget.cpp:22:23: error: SDL_image.h: No such file or directory
layout.h:50: error: expected ‘,’ or ‘...’ before ‘width’
layout.h:50: error: ISO C++ forbids declaration of ‘Uint16’ with no type
layout.h:58: error: ‘Uint16’ does not name a type
layout.h: In constructor ‘SDLwidgets::FreeLayout::FreeLayout(SDLwidgets::WidgetComposite*)’:
layout.h:61: error: class ‘SDLwidgets::FreeLayout’ does not have any field named ‘_width’
layout.h:61: error: class ‘SDLwidgets::FreeLayout’ does not have any field named ‘_height’
layout.h: In member function ‘virtual int SDLwidgets::FreeLayout::getWidth() const’:
layout.h:65: error: ‘_width’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::FreeLayout::getHeight() const’:
layout.h:66: error: ‘_height’ was not declared in this scope
layout.h: At global scope:
layout.h:75: error: ‘Uint16’ does not name a type
layout.h:76: error: ‘Uint16’ does not name a type
layout.h:77: error: ‘Uint16’ does not name a type
layout.h:84: error: ‘Uint16’ has not been declared
layout.h:88: error: ‘Uint16’ has not been declared
layout.h: In constructor ‘SDLwidgets::VerticalLayout::VerticalLayout(SDLwidgets::WidgetComposite*)’:
layout.h:81: error: class ‘SDLwidgets::VerticalLayout’ does not have any field named ‘_border_spacing’layout.h:81: error: class ‘SDLwidgets::VerticalLayout’ does not have any field named ‘_spacing’
layout.h: In member function ‘void SDLwidgets::VerticalLayout::setBorderSpacing(int)’:
layout.h:85: error: ‘_border_spacing’ was not declared in this scope
layout.h: In member function ‘void SDLwidgets::VerticalLayout::setSpacing(int)’:
layout.h:89: error: ‘_spacing’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::VerticalLayout::getWidth() const’:
layout.h:96: error: ‘_width’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::VerticalLayout::getHeight() const’:
layout.h:97: error: ‘_height’ was not declared in this scope
layout.h: At global scope:
layout.h:104: error: ‘Uint16’ does not name a type
layout.h:105: error: ‘Uint16’ does not name a type
layout.h:112: error: ‘Uint16’ has not been declared
layout.h:123: error: expected ‘,’ or ‘...’ before ‘width’
layout.h:123: error: ISO C++ forbids declaration of ‘Uint16’ with no type
layout.h: In constructor ‘SDLwidgets::HorizontalLayout::HorizontalLayout(SDLwidgets::WidgetComposite*)’:
layout.h:109: error: class ‘SDLwidgets::HorizontalLayout’ does not have any field named ‘_spacing’
layout.h: In member function ‘void SDLwidgets::HorizontalLayout::setSpacing(int)’:
layout.h:113: error: ‘_spacing’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::HorizontalLayout::getWidth() const’:
layout.h:120: error: ‘_width’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::HorizontalLayout::getHeight() const’:
layout.h:121: error: ‘_height’ was not declared in this scope
layout.h: At global scope:
layout.h:129: error: ‘Uint16’ was not declared in this scope
layout.h:129: error: template argument 1 is invalid
layout.h:129: error: template argument 2 is invalid
layout.h:130: error: ‘Uint16’ was not declared in this scope
layout.h:130: error: template argument 1 is invalid
layout.h:130: error: template argument 2 is invalid
layout.h:132: error: ‘Uint16’ does not name a type
layout.h:133: error: ‘Uint16’ does not name a type
layout.h:134: error: ‘Uint16’ does not name a type
layout.h:136: error: ‘Uint16’ has not been declared
layout.h:143: error: ‘Uint16’ has not been declared
layout.h:147: error: ‘Uint16’ has not been declared
layout.h: In constructor ‘SDLwidgets::TableLayout::TableLayout(SDLwidgets::WidgetComposite*, int)’:
layout.h:139: error: class ‘SDLwidgets::TableLayout’ does not have any field named ‘_number_columns’
layout.h:140: error: class ‘SDLwidgets::TableLayout’ does not have any field named ‘_horizontal_spacing’
layout.h:140: error: class ‘SDLwidgets::TableLayout’ does not have any field named ‘_vertical_spacing’layout.h: In member function ‘void SDLwidgets::TableLayout::setHorizontalSpacing(int)’:
layout.h:144: error: ‘_horizontal_spacing’ was not declared in this scope
layout.h: In member function ‘void SDLwidgets::TableLayout::setVerticalSpacing(int)’:
layout.h:148: error: ‘_vertical_spacing’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::TableLayout::getWidth() const’:
layout.h:154: error: ‘_width’ was not declared in this scope
layout.h: In member function ‘virtual int SDLwidgets::TableLayout::getHeight() const’:
layout.h:155: error: ‘_height’ was not declared in this scope
widget.h: At global scope:
widget.h:36: error: ‘Sint16’ does not name a type
widget.h:37: error: ‘Uint16’ does not name a type
widget.h:38: error: ‘Uint16’ does not name a type
widget.h:39: error: ‘Uint16’ does not name a type
widget.h:41: error: ‘SDL_Color’ does not name a type
widget.h:44: error: ‘SDL_Color’ does not name a type
widget.h:52: error: expected ‘,’ or ‘...’ before ‘pos_x’
widget.h:52: error: ISO C++ forbids declaration of ‘Sint16’ with no type
widget.h:56: error: ‘Sint16’ has not been declared
widget.h:56: error: ‘Sint16’ has not been declared
widget.h:60: error: ‘Sint16’ has not been declared
widget.h:60: error: ‘Sint16’ has not been declared
widget.h:61: error: expected ‘,’ or ‘...’ before ‘min_width’
widget.h:61: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:64: error: ‘Uint16’ does not name a type
widget.h:67: error: expected ‘,’ or ‘...’ before ‘min_height’
widget.h:67: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:70: error: ‘Uint16’ does not name a type
widget.h:73: error: expected ‘,’ or ‘...’ before ‘max_width’
widget.h:73: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:76: error: ‘Uint16’ does not name a type
widget.h:79: error: expected ‘,’ or ‘...’ before ‘max_height’
widget.h:79: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:82: error: ‘Uint16’ does not name a type
widget.h:85: error: expected ‘,’ or ‘...’ before ‘width’
widget.h:85: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:91: error: expected ‘,’ or ‘...’ before ‘height’
widget.h:91: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:113: error: expected ‘,’ or ‘...’ before ‘&’ token
widget.h:113: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
widget.h:116: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
widget.h:116: error: ‘SDL_Color’ declared as a ‘virtual’ field
widget.h:116: error: expected ‘;’ before ‘&’ token
widget.h:119: error: expected `;' before ‘virtual’
widget.h:119: error: ‘SDL_Surface’ has not been declared
widget.h:120: error: ‘SDL_Surface’ has not been declared
widget.h:126: error: ‘Uint16’ has not been declared
widget.h:126: error: ‘Uint16’ has not been declared
widget.h:127: error: ‘SDL_Event’ has not been declared
widget.h:135: error: ‘SDL_Color’ has not been declared
widget.h: In member function ‘virtual void SDLwidgets::Widget::setPosition(int)’:
widget.h:53: error: ‘_pos_x’ was not declared in this scope
widget.h:53: error: ‘pos_x’ was not declared in this scope
widget.h:54: error: ‘_pos_y’ was not declared in this scope
widget.h:54: error: ‘pos_y’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::getPosition(int&, int&) const’:
widget.h:57: error: ‘_pos_x’ was not declared in this scope
widget.h:58: error: ‘_pos_y’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setMinWidth(int)’:
widget.h:62: error: ‘_min_width’ was not declared in this scope
widget.h:62: error: ‘min_width’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setMinHeight(int)’:
widget.h:68: error: ‘_min_height’ was not declared in this scope
widget.h:68: error: ‘min_height’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setMaxWidth(int)’:
widget.h:74: error: ‘_max_width’ was not declared in this scope
widget.h:74: error: ‘max_width’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setMaxHeight(int)’:
widget.h:80: error: ‘_max_height’ was not declared in this scope
widget.h:80: error: ‘max_height’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setWidth(int)’:
widget.h:86: error: ‘_width’ was not declared in this scope
widget.h:86: error: ‘width’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setHeight(int)’:
widget.h:92: error: ‘_height’ was not declared in this scope
widget.h:92: error: ‘height’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::Widget::setColor(int)’:
widget.h:114: error: ‘_color’ was not declared in this scope
widget.h:114: error: ‘color’ was not declared in this scope
widget.h: In member function ‘virtual int SDLwidgets::Widget::getWidth() const’:
widget.h:124: error: ‘_width’ was not declared in this scope
widget.h: In member function ‘virtual int SDLwidgets::Widget::getHeight() const’:
widget.h:125: error: ‘_height’ was not declared in this scope
widget.h: At global scope:
widget.h:140: error: ‘SDL_Surface’ has not been declared
widget.h:154: error: ‘SDL_Surface’ has not been declared
widget.h:155: error: ‘SDL_Surface’ has not been declared
widget.h:166: error: expected ‘,’ or ‘...’ before ‘width’
widget.h:166: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:176: error: expected ‘,’ or ‘...’ before ‘height’
widget.h:176: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:185: error: ‘SDL_Event’ has not been declared
widget.h: In member function ‘virtual void SDLwidgets::WidgetComposite::setWidth(int)’:
widget.h:167: error: ‘width’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::WidgetComposite::setHeight(int)’:
widget.h:177: error: ‘height’ was not declared in this scope
widget.h: At global scope:
widget.h:216: error: ‘SDL_Event’ has not been declared
widget.h:246: error: expected ‘,’ or ‘...’ before ‘pos_x’
widget.h:246: error: ISO C++ forbids declaration of ‘Sint16’ with no type
widget.h:249: error: ‘Sint16’ has not been declared
widget.h:249: error: ‘Sint16’ has not been declared
widget.h:252: error: ‘Sint16’ has not been declared
widget.h:252: error: ‘Sint16’ has not been declared
widget.h:255: error: expected ‘,’ or ‘...’ before ‘max_width’
widget.h:255: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:258: error: ‘Uint16’ does not name a type
widget.h:261: error: expected ‘,’ or ‘...’ before ‘max_height’
widget.h:261: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:264: error: ‘Uint16’ does not name a type
widget.h:267: error: expected ‘,’ or ‘...’ before ‘width’
widget.h:267: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:270: error: expected ‘,’ or ‘...’ before ‘height’
widget.h:270: error: ISO C++ forbids declaration of ‘Uint16’ with no type
widget.h:273: error: expected ‘,’ or ‘...’ before ‘&’ token
widget.h:273: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
widget.h:276: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
widget.h:276: error: ‘SDL_Color’ declared as a ‘virtual’ field
widget.h:276: error: expected ‘;’ before ‘&’ token
widget.h:279: error: expected `;' before ‘virtual’
widget.h:279: error: ‘SDL_Surface’ has not been declared
widget.h:282: error: ‘SDL_Surface’ has not been declared
widget.h:300: error: ‘SDL_Event’ has not been declared
widget.h: In member function ‘virtual void SDLwidgets::WidgetProxy::setPosition(int)’:
widget.h:247: error: ‘pos_x’ was not declared in this scope
widget.h:247: error: ‘pos_y’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::WidgetProxy::setMaxWidth(int)’:
widget.h:256: error: ‘max_width’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::WidgetProxy::setMaxHeight(int)’:
widget.h:262: error: ‘max_height’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::WidgetProxy::setWidth(int)’:
widget.h:268: error: ‘width’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::WidgetProxy::setHeight(int)’:
widget.h:271: error: ‘height’ was not declared in this scope
widget.h: In member function ‘virtual void SDLwidgets::WidgetProxy::setColor(int)’:
widget.h:274: error: ‘color’ was not declared in this scope
backgroundwidget.h: At global scope:
backgroundwidget.h:30: error: ‘Uint8’ does not name a type
backgroundwidget.h:31: error: ISO C++ forbids declaration of ‘SDL_Surface’ with no type
backgroundwidget.h:31: error: expected ‘;’ before ‘*’ token
backgroundwidget.h:48: error: expected ‘,’ or ‘...’ before ‘&’ token
backgroundwidget.h:48: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
backgroundwidget.h:65: error: expected ‘,’ or ‘...’ before ‘&’ token
backgroundwidget.h:65: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
backgroundwidget.h:67: error: ‘SDL_Surface’ has not been declared
backgroundwidget.h:68: error: expected ‘,’ or ‘...’ before ‘width’
backgroundwidget.h:68: error: ISO C++ forbids declaration of ‘Uint16’ with no type
backgroundwidget.h:69: error: expected ‘,’ or ‘...’ before ‘min_width’
backgroundwidget.h:69: error: ISO C++ forbids declaration of ‘Uint16’ with no type
backgroundwidget.h:70: error: expected ‘,’ or ‘...’ before ‘height’
backgroundwidget.h:70: error: ISO C++ forbids declaration of ‘Uint16’ with no type
backgroundwidget.h: In constructor ‘SDLwidgets::BackgroundWidget::BackgroundWidget(SDLwidgets::Widget*)’:
backgroundwidget.h:34: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_alpha’
backgroundwidget.h:34: error: ‘SDL_ALPHA_TRANSPARENT’ was not declared in this scope
backgroundwidget.h:34: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_image’
backgroundwidget.h:36: error: no matching function for call to ‘SDLwidgets::Widget::setPosition(int, int)’
widget.h:52: note: candidates are: virtual void SDLwidgets::Widget::setPosition(int)
backgroundwidget.h:37: error: ‘_min_width’ was not declared in this scope
backgroundwidget.h:37: error: ‘class SDLwidgets::Widget’ has no member named ‘getMinWidth’
backgroundwidget.h:38: error: ‘_min_height’ was not declared in this scope
backgroundwidget.h:38: error: ‘class SDLwidgets::Widget’ has no member named ‘getMinHeight’
backgroundwidget.h:39: error: ‘_max_width’ was not declared in this scope
backgroundwidget.h:39: error: ‘class SDLwidgets::Widget’ has no member named ‘getMaxWidth’
backgroundwidget.h:40: error: ‘_max_height’ was not declared in this scope
backgroundwidget.h:40: error: ‘class SDLwidgets::Widget’ has no member named ‘getMaxHeight’
backgroundwidget.h:41: error: ‘_width’ was not declared in this scope
backgroundwidget.h:42: error: ‘_height’ was not declared in this scope
backgroundwidget.h:44: error: ‘_color’ was not declared in this scope
backgroundwidget.h: In constructor ‘SDLwidgets::BackgroundWidget::BackgroundWidget(SDLwidgets::Widget*, int)’:
backgroundwidget.h:49: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_alpha’
backgroundwidget.h:49: error: ‘alpha’ was not declared in this scope
backgroundwidget.h:49: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_image’
backgroundwidget.h:51: error: no matching function for call to ‘SDLwidgets::Widget::setPosition(int, int)’
widget.h:52: note: candidates are: virtual void SDLwidgets::Widget::setPosition(int)
backgroundwidget.h:52: error: ‘_min_width’ was not declared in this scope
backgroundwidget.h:52: error: ‘class SDLwidgets::Widget’ has no member named ‘getMinWidth’
backgroundwidget.h:53: error: ‘_min_height’ was not declared in this scope
backgroundwidget.h:53: error: ‘class SDLwidgets::Widget’ has no member named ‘getMinHeight’
backgroundwidget.h:54: error: ‘_max_width’ was not declared in this scope
backgroundwidget.h:54: error: ‘class SDLwidgets::Widget’ has no member named ‘getMaxWidth’
backgroundwidget.h:55: error: ‘_max_height’ was not declared in this scope
backgroundwidget.h:55: error: ‘class SDLwidgets::Widget’ has no member named ‘getMaxHeight’
backgroundwidget.h:56: error: ‘_width’ was not declared in this scope
backgroundwidget.h:57: error: ‘_height’ was not declared in this scope
backgroundwidget.h:59: error: ‘_color’ was not declared in this scope
backgroundwidget.h:59: error: ‘color’ was not declared in this scope
graphics.h: At global scope:
graphics.h:30: error: ‘SDL_Surface’ has not been declared
graphics.h:31: error: ‘Uint32’ has not been declared
graphics.h:64: error: ‘SDL_Surface’ has not been declared
graphics.h:65: error: expected ‘,’ or ‘...’ before ‘*’ token
graphics.h:65: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
graphics.h:65: error: ‘static void SDLwidgets::Graphics::putPixel(int*, int, int, int)’ cannot be overloaded
graphics.h:31: error: with ‘static void SDLwidgets::Graphics::putPixel(int*, int, int, int)’
graphics.h:70: error: ‘SDL_Surface’ has not been declared
graphics.h:71: error: expected ‘,’ or ‘...’ before ‘*’ token
graphics.h:71: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
graphics.h:72: error: ‘SDL_Surface’ has not been declared
graphics.h:72: error: ‘SDL_Rect’ has not been declared
graphics.h:73: error: ‘SDL_Color’ has not been declared
graphics.h:73: error: ‘Uint8’ has not been declared
graphics.h: In static member function ‘static void SDLwidgets::Graphics::putPixel(int*, int, int, int)’:
graphics.h:33: error: request for member ‘format’ in ‘* surface’, which is of non-class type ‘int’
graphics.h:35: error: ‘Uint8’ was not declared in this scope
graphics.h:35: error: ‘p’ was not declared in this scope
graphics.h:35: error: expected type-specifier before ‘Uint8’
graphics.h:35: error: expected `>' before ‘Uint8’
graphics.h:35: error: expected `(' before ‘Uint8’
graphics.h:35: error: expected primary-expression before ‘>’ token
graphics.h:35: error: request for member ‘pixels’ in ‘* surface’, which is of non-class type ‘int’
graphics.h:36: error: request for member ‘pitch’ in ‘* surface’, which is of non-class type ‘int’
graphics.h:36: error: expected `)' before ‘;’ token
graphics.h:44: error: expected type-specifier before ‘Uint16’
graphics.h:44: error: expected `>' before ‘Uint16’
graphics.h:44: error: expected `(' before ‘Uint16’
graphics.h:44: error: ‘Uint16’ was not declared in this scope
graphics.h:44: error: expected primary-expression before ‘>’ token
graphics.h:44: error: expected `)' before ‘;’ token
graphics.h:48: error: ‘SDL_BYTEORDER’ was not declared in this scope
graphics.h:48: error: ‘SDL_BIG_ENDIAN’ was not declared in this scope
graphics.h:60: error: expected type-specifier before ‘Uint32’
graphics.h:60: error: expected `>' before ‘Uint32’
graphics.h:60: error: expected `(' before ‘Uint32’
graphics.h:60: error: ‘Uint32’ was not declared in this scope
graphics.h:60: error: expected primary-expression before ‘>’ token
graphics.h:60: error: expected `)' before ‘;’ token
graphics.h: In static member function ‘static void SDLwidgets::Graphics::putPixel(int*, int, int, int)’:
graphics.h:66: error: ‘Uint32’ was not declared in this scope
graphics.h:66: error: expected `;' before ‘pixelValue’
graphics.h:68: error: ‘pixelValue’ was not declared in this scope
backgroundwidget.cpp: In constructor ‘SDLwidgets::BackgroundWidget::BackgroundWidget(SDLwidgets::Widget*, const char*)’:
backgroundwidget.cpp:30: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_alpha’
backgroundwidget.cpp:30: error: ‘SDL_ALPHA_OPAQUE’ was not declared in this scope
backgroundwidget.cpp:32: error: no matching function for call to ‘SDLwidgets::Widget::setPosition(int, int)’
widget.h:52: note: candidates are: virtual void SDLwidgets::Widget::setPosition(int)
backgroundwidget.cpp:33: error: ‘_min_width’ was not declared in this scope
backgroundwidget.cpp:33: error: ‘class SDLwidgets::Widget’ has no member named ‘getMinWidth’
backgroundwidget.cpp:34: error: ‘_min_height’ was not declared in this scope
backgroundwidget.cpp:34: error: ‘class SDLwidgets::Widget’ has no member named ‘getMinHeight’
backgroundwidget.cpp:35: error: ‘_max_width’ was not declared in this scope
backgroundwidget.cpp:35: error: ‘class SDLwidgets::Widget’ has no member named ‘getMaxWidth’
backgroundwidget.cpp:36: error: ‘_max_height’ was not declared in this scope
backgroundwidget.cpp:36: error: ‘class SDLwidgets::Widget’ has no member named ‘getMaxHeight’
backgroundwidget.cpp:37: error: ‘_width’ was not declared in this scope
backgroundwidget.cpp:38: error: ‘_height’ was not declared in this scope
backgroundwidget.cpp:40: error: ‘_color’ was not declared in this scope
backgroundwidget.cpp:43: error: ‘_image’ was not declared in this scope
backgroundwidget.cpp:43: error: ‘IMG_Load’ was not declared in this scope
backgroundwidget.cpp: In constructor ‘SDLwidgets::BackgroundWidget::BackgroundWidget(int, int)’:
backgroundwidget.cpp:47: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_alpha’
backgroundwidget.cpp:47: error: ‘SDL_ALPHA_OPAQUE’ was not declared in this scope
backgroundwidget.cpp:47: error: class ‘SDLwidgets::BackgroundWidget’ does not have any field named ‘_image’
backgroundwidget.cpp:48: error: ‘_min_width’ was not declared in this scope
backgroundwidget.cpp:49: error: ‘_max_width’ was not declared in this scope
backgroundwidget.cpp:50: error: ‘_width’ was not declared in this scope
backgroundwidget.cpp:51: error: ‘_min_height’ was not declared in this scope
backgroundwidget.cpp:52: error: ‘_max_height’ was not declared in this scope
backgroundwidget.cpp:53: error: ‘_height’ was not declared in this scope
backgroundwidget.cpp: At global scope:
backgroundwidget.cpp:56: error: variable or field ‘draw’ declared void
backgroundwidget.cpp:56: error: ‘int SDLwidgets::BackgroundWidget::draw’ is not a static member of ‘class SDLwidgets::BackgroundWidget’
backgroundwidget.cpp:56: error: ‘SDL_Surface’ was not declared in this scope
backgroundwidget.cpp:56: error: ‘surface’ was not declared in this scope
backgroundwidget.cpp:56: error: expected ‘,’ or ‘;’ before ‘{’ token
backgroundwidget.cpp:105: error: expected ‘,’ or ‘...’ before ‘&’ token
backgroundwidget.cpp:105: error: ISO C++ forbids declaration of ‘SDL_Color’ with no type
backgroundwidget.cpp: In member function ‘virtual void SDLwidgets::BackgroundWidget::setColor(int)’:
backgroundwidget.cpp:106: error: ‘color’ was not declared in this scope
backgroundwidget.cpp: In member function ‘virtual void SDLwidgets::BackgroundWidget::setAlpha(int)’:
backgroundwidget.cpp:110: error: ‘_alpha’ was not declared in this scope
backgroundwidget.cpp: At global scope:
backgroundwidget.cpp:113: error: expected ‘,’ or ‘...’ before ‘width’
backgroundwidget.cpp:113: error: ISO C++ forbids declaration of ‘Uint16’ with no type
backgroundwidget.cpp: In member function ‘virtual void SDLwidgets::BackgroundWidget::setWidth(int)’:
backgroundwidget.cpp:114: error: ‘width’ was not declared in this scope
backgroundwidget.cpp:114: error: ‘_min_width’ was not declared in this scope
backgroundwidget.cpp:120: error: ‘_width’ was not declared in this scope
backgroundwidget.cpp:122: error: ‘_height’ was not declared in this scope
backgroundwidget.cpp: At global scope:
backgroundwidget.cpp:126: error: expected ‘,’ or ‘...’ before ‘min_width’
backgroundwidget.cpp:126: error: ISO C++ forbids declaration of ‘Uint16’ with no type
backgroundwidget.cpp: In member function ‘virtual void SDLwidgets::BackgroundWidget::setMinWidth(int)’:
backgroundwidget.cpp:127: error: ‘_min_width’ was not declared in this scope
backgroundwidget.cpp:127: error: ‘min_width’ was not declared in this scope
backgroundwidget.cpp:128: error: ‘_width’ was not declared in this scope
backgroundwidget.cpp: At global scope:
backgroundwidget.cpp:133: error: expected ‘,’ or ‘...’ before ‘height’
backgroundwidget.cpp:133: error: ISO C++ forbids declaration of ‘Uint16’ with no type
backgroundwidget.cpp: In member function ‘virtual void SDLwidgets::BackgroundWidget::setHeight(int)’:
backgroundwidget.cpp:134: error: ‘_height’ was not declared in this scope
backgroundwidget.cpp:134: error: ‘height’ was not declared in this scope
backgroundwidget.cpp:138: error: ‘_width’ was not declared in this scope
backgroundwidget.cpp: In member function ‘virtual void SDLwidgets::BackgroundWidget::doLayout()’:
backgroundwidget.cpp:145: error: ‘_min_width’ was not declared in this scope
backgroundwidget.cpp:146: error: ‘_width’ was not declared in this scope
backgroundwidget.cpp:147: error: ‘_min_height’ was not declared in this scope
backgroundwidget.cpp:148: error: ‘_height’ was not declared in this scope
make[1]: *** [backgroundwidget.o] Error 1
make[1]: Leaving directory `/home/hansoffate/Desktop/wop-0.4.3/sdlwidgets'
make: *** [all] Error 2

```

---

### Post by Gannin on 2006-07-09
It looks like you need both the SDL and SDL_image development libraries installed, and it looks like you have neither.

---

### Post by hansoffate on 2006-07-09
I got one of the packets.  I tried getting the libsdl-ttf2.0 but it didn't work.  What else do i need?

```
hansoffate@hansoffate-desktop:~/Desktop/wop-0.4.3$ make
cd sdlwidgets; make
make[1]: Entering directory `/home/hansoffate/Desktop/wop-0.4.3/sdlwidgets'
g++ -Wall -Wshadow -Wsign-compare -Wparentheses -Wconversion -g -O3 -ansi -I/usr/include/SDL -D_REENTRANT -c backgroundwidget.cpp -o backgroundwidget.o
g++ -Wall -Wshadow -Wsign-compare -Wparentheses -Wconversion -g -O3 -ansi -I/usr/include/SDL -D_REENTRANT -c borderwidget.cpp -o borderwidget.o
g++ -Wall -Wshadow -Wsign-compare -Wparentheses -Wconversion -g -O3 -ansi -I/usr/include/SDL -D_REENTRANT -c button.cpp -o button.o
In file included from button.h:26,
                 from button.cpp:21:
textlabel.h:26:21: error: SDL_ttf.h: No such file or directory
textlabel.h:40: error: ISO C++ forbids declaration of &#8216;TTF_Font&#8217; with no type
textlabel.h:40: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[1]: *** [button.o] Error 1
make[1]: Leaving directory `/home/hansoffate/Desktop/wop-0.4.3/sdlwidgets'
make: *** [all] Error 2
hansoffate@hansoffate-desktop:~/Desktop/wop-0.4.3$

```

Thanks
-Hans

---

### Post by hansoffate on 2006-07-09
bump

---

### Post by simplyw00x on 2006-07-10
```
sudo apt-get install libsdl-image2.0-dev libsdl-mixer2.0-dev libsdl-net2.0-dev libsdl-ttf2.0-dev zlib1g-dev
```

That should be a start.

---

### Post by hansoffate on 2006-07-29
What Repos should i use?  Apt-get can't find it with my repos right now.

---

### Post by Gannin on 2006-07-29
What version of Ubuntu are you using?

---

