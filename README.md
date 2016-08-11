# intake-spigot
A Spigot bridge for [sk89q/Intake](https://github.com/sk89q/Intake). 
Delivered as standalone plugin (`intake-spigot-x.y.z-plugin.jar`) or simple Maven dependency (if you prefer the shades (⌐■_■)).

The standalone plugin currently comes with a [customer fork of Intake](https://github.com/xxyy/Intake) that has
some fixes necessary for this to work. However, there are pending 
[pull](https://github.com/sk89q/Intake/pull/26) [requests](https://github.com/sk89q/Intake/pull/25) to upstream.
Once upstream accepts the changes of introduces comparable features, the dependency will be changed back.
Namely, upstream doesn't allow more than a single classifier annotation per parameter type and their
`TextProvider` is broken.

# Features

You might have been wondering what this bridge can do for you. For this, you have to know the initial motivation:
When I first wanted to try Intake, I found out the hard way that it needs quite a bit of boilerplate code when
used with Bukkit, especially compared to the old [sk89q-command-framework](https://github.com/OvercastNetwork/sk89q-command-framework].

Therefore, I created a more-or-less abstract library for what I needed. This includes:

* basic registration of Intake commands without any `plugin.yml` hassle
* automatic creation of helpful help messages from command metadata with JSON tooltips and `<command> help` subcommands
* extendable error handling
* custom unchecked message exceptions (`CommandExitMessage`)
* automatic translation of Intake messages to other languages (German is included, feel free to PR more!)
* parameter providers for common things used in commands (such as `@ItemInHand ItemStack`, `@Merged  @Colored String`, `CommandSender`, `@Sender Player`, `@Online Player`)
* a intuitive builder framework
* all that without shading anything

# Installation

Installing this as a server owner is as easy as dropping the
[current plugin jar](https://ci.l1t.li/job/public~intake-spigot/lastRelease/) into your server's plugins folder.

Installing this as a developer is slightly more complicated, since this project isn't being deployed into Maven Central.

## Maven

````xml
<repositories>
  <repository>
    <id>xxyy-repo</id>
    <url>https://repo.l1t.li/xxyy-public/</url>
  </repository>
</repositories>
<dependencies>
  <dependency>
    <groupId>li.l1t.common</groupId>
    <artifactId>intake-spigot</artifactId>
    <version>${intake-spigot.version}</version>
    <!-- Sorry, you'll have to look the latest release up yourself, since this project releases often-ish -->
  </dependency>
</dependencies>
````

## Gradle

Same, just with Gradle syntax.

# Contributing

All contributions welcome, including further translations! 

This project uses standard IntelliJ code style. Format your code with `Alt+Shift+L`. 

I recommend that you read ['Clean Code' by the awesome Robert C. Martin](https://www.google.at/webhp?q=clean+code+pdf#newwindow=1&q=clean+code+pdf).

# License

This project is licensed under LGPL, mainly because it includes two lines from Intake that I had to copy 
(y u make everything package-private).

See the included `LICENSE.txt` file for details.
