---
title: "Error while installing Stage 3.2.2"
date: 2013-08-24
forum: Education &amp; Science
---

### Post by tahir2 on 2013-08-24
Hi guys ,

i am new to linux and i am trying to install player/stage , i had sucess in installing player but while using make command in stage i got the following error . 

```
CMakeFiles/stagebinary.dir/main.o: In function `main':
main.cc:(.text.startup+0x304): undefined reference to `Fl::run()'
libstage.so.3.2.2: undefined reference to `png_create_info_struct'
libstage.so.3.2.2: undefined reference to `gl_font(int, int)'
libstage.so.3.2.2: undefined reference to `Fl::e_number'
libstage.so.3.2.2: undefined reference to `Fl_Group::begin()'
libstage.so.3.2.2: undefined reference to `Fl_Text_Buffer::insert(int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Window::size_range_()'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::show()'
libstage.so.3.2.2: undefined reference to `vtable for Fl_Gl_Window'
libstage.so.3.2.2: undefined reference to `Fl_Widget::label(char const*)'
libstage.so.3.2.2: undefined reference to `vtable for Fl_Menu_Bar'
libstage.so.3.2.2: undefined reference to `Fl_File_Chooser::shown()'
libstage.so.3.2.2: undefined reference to `Fl_Text_Buffer::Fl_Text_Buffer(int)'
libstage.so.3.2.2: undefined reference to `Fl_Group::find(Fl_Widget const*) const'
libstage.so.3.2.2: undefined reference to `typeinfo for Fl_Window'
libstage.so.3.2.2: undefined reference to `Fl_Widget::window() const'
libstage.so.3.2.2: undefined reference to `png_set_IHDR'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::flush()'
libstage.so.3.2.2: undefined reference to `png_set_rows'
libstage.so.3.2.2: undefined reference to `png_destroy_write_struct'
libstage.so.3.2.2: undefined reference to `Fl::add_idle(void (*)(void*), void*)'
libstage.so.3.2.2: undefined reference to `Fl_Window::handle(int)'
libstage.so.3.2.2: undefined reference to `Fl_Text_Display::Fl_Text_Display(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `png_init_io'
libstage.so.3.2.2: undefined reference to `vtable for Fl_Box'
libstage.so.3.2.2: undefined reference to `Fl_File_Chooser::ok_label(char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Shared_Image::release()'
libstage.so.3.2.2: undefined reference to `Fl::repeat_timeout(double, void (*)(void*), void*)'
libstage.so.3.2.2: undefined reference to `Fl_File_Chooser::~Fl_File_Chooser()'
libstage.so.3.2.2: undefined reference to `gl_width(char const*)'
libstage.so.3.2.2: undefined reference to `Fl::e_x'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::draw_overlay()'
libstage.so.3.2.2: undefined reference to `Fl_Widget::Fl_Widget(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl::e_keysym'
libstage.so.3.2.2: undefined reference to `Fl_Button::value(int)'
libstage.so.3.2.2: undefined reference to `png_write_png'
libstage.so.3.2.2: undefined reference to `Fl::scheme(char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Window::~Fl_Window()'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::invalidate()'
libstage.so.3.2.2: undefined reference to `Fl_Widget::redraw()'
libstage.so.3.2.2: undefined reference to `fl_alert(char const*, ...)'
libstage.so.3.2.2: undefined reference to `fl_old_shortcut(char const*)'
libstage.so.3.2.2: undefined reference to `Fl::delete_widget(Fl_Widget*)'
libstage.so.3.2.2: undefined reference to `Fl_Check_Button::Fl_Check_Button(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Text_Buffer::~Fl_Text_Buffer()'
libstage.so.3.2.2: undefined reference to `Fl_Shared_Image::get(char const*, int, int)'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::resize(int, int, int, int)'
libstage.so.3.2.2: undefined reference to `Fl_Window::hide()'
libstage.so.3.2.2: undefined reference to `fl_register_images()'
libstage.so.3.2.2: undefined reference to `gl_draw(char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Group::end()'
libstage.so.3.2.2: undefined reference to `Fl_Window::Fl_Window(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl_PNG_Image::Fl_PNG_Image(char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Scroll::Fl_Scroll(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::hide()'
libstage.so.3.2.2: undefined reference to `Fl_Widget::default_callback(Fl_Widget*, void*)'
libstage.so.3.2.2: undefined reference to `Fl_File_Chooser::value(int)'
libstage.so.3.2.2: undefined reference to `Fl::wait()'
libstage.so.3.2.2: undefined reference to `Fl::e_y'
libstage.so.3.2.2: undefined reference to `gl_draw(char const*, int, int, int, int, Fl_Align)'
libstage.so.3.2.2: undefined reference to `Fl::check()'
libstage.so.3.2.2: undefined reference to `Fl_Text_Buffer::text(char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Menu_::add(char const*, int, void (*)(Fl_Widget*, void*), void*, int)'
libstage.so.3.2.2: undefined reference to `Fl::remove_timeout(void (*)(void*), void*)'
libstage.so.3.2.2: undefined reference to `Fl_Window::draw()'
libstage.so.3.2.2: undefined reference to `png_create_write_struct'
libstage.so.3.2.2: undefined reference to `Fl_Window::flush()'
libstage.so.3.2.2: undefined reference to `Fl_Scroll::clear()'
libstage.so.3.2.2: undefined reference to `typeinfo for Fl_Gl_Window'
libstage.so.3.2.2: undefined reference to `Fl_Window::show()'
libstage.so.3.2.2: undefined reference to `Fl_Text_Display::buffer(Fl_Text_Buffer*)'
libstage.so.3.2.2: undefined reference to `Fl_File_Chooser::show()'
libstage.so.3.2.2: undefined reference to `Fl_Menu_::global()'
libstage.so.3.2.2: undefined reference to `Fl_Window::label(char const*)'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::~Fl_Gl_Window()'
libstage.so.3.2.2: undefined reference to `Fl::e_state'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::init()'
libstage.so.3.2.2: undefined reference to `Fl_Menu_::Fl_Menu_(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl::e_dy'
libstage.so.3.2.2: undefined reference to `Fl::add_timeout(double, void (*)(void*), void*)'
libstage.so.3.2.2: undefined reference to `vtable for Fl_Return_Button'
libstage.so.3.2.2: undefined reference to `Fl_Gl_Window::make_current()'
libstage.so.3.2.2: undefined reference to `Fl_Window::Fl_Window(int, int, char const*)'
libstage.so.3.2.2: undefined reference to `fl_height()'
libstage.so.3.2.2: undefined reference to `gl_height()'
libstage.so.3.2.2: undefined reference to `Fl_Button::Fl_Button(int, int, int, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl_File_Chooser::Fl_File_Chooser(char const*, char const*, int, char const*)'
libstage.so.3.2.2: undefined reference to `Fl::remove_idle(void (*)(void*), void*)'
libstage.so.3.2.2: undefined reference to `Fl_Window::resize(int, int, int, int)'
libstage.so.3.2.2: undefined reference to `fl_choice(char const*, char const*, char const*, char const*, ...)'
collect2: ld returned 1 exit status
make[2]: *** [libstage/stage] Error 1
make[1]: *** [libstage/CMakeFiles/stagebinary.dir/all] Error 2
make: *** [all] Error 2


```


i also made changes in the CMakelists.txt i replace following lines 
```
[FONT=Arial]SET (CMAKE_CXX_FLAGS_RELEASE " -O3 -DNDEBUG ${WALL} " CACHE INTERNAL "C Flags for release" FORCE)[/FONT]
[FONT=Arial]SET (CMAKE_CXX_FLAGS_DEBUG " -ggdb ${WALL} " CACHE INTERNAL "C Flags for debug" FORCE)[/FONT]
[FONT=Arial]SET (CMAKE_CXX_FLAGS_PROFILE " -O3 -ggdb -pg ${WALL} " CACHE INTERNAL "C Flags for profile" FORCE)[/FONT]


```

with these lines 

```
[FONT=Arial]SET (CMAKE_CXX_FLAGS_RELEASE " -O3 -DNDEBUG -Wl,--no-as-needed" CACHE INTERNAL "C Flags for release" FORCE)[/FONT]
[FONT=Arial]SET (CMAKE_CXX_FLAGS_DEBUG " -ggdb -Wl,--no-as-needed " CACHE INTERNAL "C Flags for debug" FORCE)[/FONT]
[FONT=Arial]SET (CMAKE_CXX_FLAGS_PROFILE " -O3 -ggdb -pg -Wl,--no-as-needed " CACHE INTERNAL "C Flags for profile" FORCE)[/FONT]


```

---

