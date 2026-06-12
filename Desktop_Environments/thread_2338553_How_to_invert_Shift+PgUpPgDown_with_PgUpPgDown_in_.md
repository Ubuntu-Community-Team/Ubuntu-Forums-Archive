---
title: "How to invert Shift+PgUp/PgDown with PgUp/PgDown in Gnome Terminal?"
date: 2016-09-29
forum: Desktop Environments
---

### Post by sbrisu on 2016-09-29
Hi All,


As per design gnome-terminal uses **Shift+Page_up / Shift+Page_down** for scrolling terminal’s buffer – this behaviour is hard-coded and I would like to make it to scroll only with **Page_up / Page_down**.


I understand they designed it this way because of the less command, and the fact that simple **Page_up / Page_down** scrolling is left for **vim** and other text editor inside the application.


Searching I found that the terminal overrides both** xkb** and** xmodmap **settings, because takes the instructions directly from **VTE** [https://github.com/GNOME/vte](https://github.com/GNOME/vte).


I am not a coder but like to try to understand how it works, and I suspect the settings I am looking for are in two places:


**vte.c** [https://github.com/GNOME/vte/blob/master/src/vte.cc](https://github.com/GNOME/vte/blob/master/src/vte.cc), in particular here:


```
        case GDK_KEY_KP_Page_Up:
        case GDK_KEY_Page_Up:
            if (m_screen == &m_normal_screen &&
                m_modifiers & GDK_SHIFT_MASK) {
                scroll_pages(-1);
                scrolled = TRUE;
                handled = TRUE;
                suppress_meta_esc = TRUE;
            }
            break;
        case GDK_KEY_KP_Page_Down:
        case GDK_KEY_Page_Down:
            if (m_screen == &m_normal_screen &&
                m_modifiers & GDK_SHIFT_MASK) {
                scroll_pages(1);
                scrolled = TRUE;
                handled = TRUE;
                suppress_meta_esc = TRUE;
            }  

```..or here in **keymap.cc**:


```
    static const struct _vte_keymap_entry _vte_keymap_GDK_Page_Up[] = {
            {cursor_all, keypad_all, 0, _VTE_CAP_CSI "5~", -1},
            {cursor_all, keypad_all, 0, X_NULL, 0},
    };


    static const struct _vte_keymap_entry _vte_keymap_GDK_Page_Down[] = {
            {cursor_all, keypad_all, 0, _VTE_CAP_CSI "6~", -1},
            {cursor_all, keypad_all, 0, X_NULL, 0},
    };



```Any lights on the above codes and how I to invert the behavior of **Shift+Page_up / Shift+Page_down** with **Page_up / Page_down**?


Many thanks in advance!

---

