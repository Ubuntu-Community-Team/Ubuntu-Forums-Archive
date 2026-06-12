---
title: "Panel Applet Idea"
date: 2009-05-12
forum: General Help
---

### Post by ninjapirate89 on 2009-05-12
Does anyone know of a panel applet similar to window list that only shows icons? I have window selector in use right now, but it's not quite what I'm wanting. I'm trying to make a basic dock using only the panel but this is the one thing I'm missing. I don't have any programming experience but it seems to me that it wouldn't be that hard to modify window list to only show icons.

Edit -> Should I have put this in the programming section?

---

### Post by Tipped OuT on 2009-05-12
Yep, you should have posted this in the Programming section. It's okay, we all make mistakes. :P

---

### Post by ninjapirate89 on 2009-05-12
> **Tipped OuT said:**
> Yep, you should have posted this in the Programming section. It's okay, we all make mistakes. :P

I wasn't sure if I should have or not when I made the thread because there may already be an applet like this made.

---

### Post by ninjapirate89 on 2009-05-12
Does anyone know where the code for the applets are saved? I wouldn't mind taking a peak under the hood.

---

### Post by ninjapirate89 on 2009-05-12
I was expecting a python script when I went searching for the code for the window list applet but I found this .glade file instead. Is this what needs to be modified to do what I want? I found it in /usr/share/gnome-panel/glade
Here is the code:
```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--*- mode: xml -*-->
<glade-interface>
  <widget class="GtkDialog" id="tasklist_properties_dialog">
    <property name="border_width">5</property>
    <property name="title" translatable="yes">Window List Preferences</property>
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
    <property name="has_separator">False</property>
    <child internal-child="vbox">
      <widget class="GtkVBox" id="dialog-vbox2">
        <property name="visible">True</property>
        <property name="spacing">2</property>
        <child>
          <widget class="GtkVBox" id="vbox1">
            <property name="visible">True</property>
            <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
            <property name="border_width">5</property>
            <property name="spacing">18</property>
            <child>
              <widget class="GtkVBox" id="vbox7">
                <property name="visible">True</property>
                <property name="spacing">6</property>
                <child>
                  <widget class="GtkLabel" id="label1">
                    <property name="visible">True</property>
                    <property name="xalign">0</property>
                    <property name="label" translatable="yes">&lt;b&gt;Window List Content&lt;/b&gt;</property>
                    <property name="use_markup">True</property>
                  </widget>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="GtkAlignment" id="alignment1">
                    <property name="visible">True</property>
                    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                    <property name="left_padding">12</property>
                    <child>
                      <widget class="GtkVBox" id="vbox9">
                        <property name="visible">True</property>
                        <property name="spacing">6</property>
                        <child>
                          <widget class="GtkRadioButton" id="show_current_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">Sh_ow windows from current workspace</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkRadioButton" id="show_all_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">Show windows from a_ll workspaces</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                            <property name="group">show_current_radio</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="expand">False</property>
              </packing>
            </child>
            <child>
              <widget class="GtkVBox" id="vbox11">
                <property name="visible">True</property>
                <property name="spacing">6</property>
                <child>
                  <widget class="GtkLabel" id="label3">
                    <property name="visible">True</property>
                    <property name="xalign">0</property>
                    <property name="label" translatable="yes">&lt;b&gt;Window Grouping&lt;/b&gt;</property>
                    <property name="use_markup">True</property>
                  </widget>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="GtkAlignment" id="alignment2">
                    <property name="visible">True</property>
                    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                    <property name="left_padding">12</property>
                    <child>
                      <widget class="GtkVBox" id="vbox12">
                        <property name="visible">True</property>
                        <property name="spacing">6</property>
                        <child>
                          <widget class="GtkRadioButton" id="never_group_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">_Never group windows</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkRadioButton" id="auto_group_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">Group windows when _space is limited</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                            <property name="group">never_group_radio</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkRadioButton" id="always_group_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">_Always group windows</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                            <property name="group">never_group_radio</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">2</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkVBox" id="vbox13">
                <property name="visible">True</property>
                <property name="spacing">6</property>
                <child>
                  <widget class="GtkLabel" id="minimized_windows_label">
                    <property name="visible">True</property>
                    <property name="xalign">0</property>
                    <property name="label" translatable="yes">&lt;b&gt;Restoring Minimized Windows&lt;/b&gt;</property>
                    <property name="use_markup">True</property>
                  </widget>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="GtkAlignment" id="alignment3">
                    <property name="visible">True</property>
                    <property name="events">GDK_POINTER_MOTION_MASK | GDK_POINTER_MOTION_HINT_MASK | GDK_BUTTON_PRESS_MASK | GDK_BUTTON_RELEASE_MASK</property>
                    <property name="left_padding">12</property>
                    <child>
                      <widget class="GtkVBox" id="vbox14">
                        <property name="visible">True</property>
                        <property name="spacing">6</property>
                        <child>
                          <widget class="GtkRadioButton" id="move_minimized_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">Restore to current _workspace</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                          </packing>
                        </child>
                        <child>
                          <widget class="GtkRadioButton" id="change_workspace_radio">
                            <property name="visible">True</property>
                            <property name="can_focus">True</property>
                            <property name="label" translatable="yes">Restore to na_tive workspace</property>
                            <property name="use_underline">True</property>
                            <property name="response_id">0</property>
                            <property name="draw_indicator">True</property>
                            <property name="group">move_minimized_radio</property>
                          </widget>
                          <packing>
                            <property name="expand">False</property>
                            <property name="fill">False</property>
                            <property name="position">1</property>
                          </packing>
                        </child>
                      </widget>
                    </child>
                  </widget>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="position">2</property>
              </packing>
            </child>
          </widget>
        </child>
        <child internal-child="action_area">
          <widget class="GtkHButtonBox" id="dialog-action_area2">
            <property name="visible">True</property>
            <property name="layout_style">GTK_BUTTONBOX_END</property>
            <child>
              <widget class="GtkButton" id="help_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="label">gtk-help</property>
                <property name="use_stock">True</property>
                <property name="response_id">-11</property>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="done_button">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="can_default">True</property>
                <property name="has_default">True</property>
                <property name="label">gtk-close</property>
                <property name="use_stock">True</property>
                <property name="response_id">0</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">GTK_PACK_END</property>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

Edit -> Nope this seems to be the preferences for window list not the code itself. I'll keep looking for it but I don't know what I'll do when I find it.

---

