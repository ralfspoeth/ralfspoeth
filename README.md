# Me, The Greyson Guy

Software for the JVM, mostly Java with some Clojure on the side.

## Active Projects

- **[greyson](https://github.com/ralfspoeth/greyson)**: a small JSON IO library for modern Java, with immutable values, records and sealed types.
- **[xldr](https://github.com/ralfspoeth/xldr)**: an _e**x**tensible **l**oa**d**e**r**_ that maps files into relational tables.

## Small Libraries

Small, focused libraries for everyday Java work.

- **[basix](https://github.com/ralfspoeth/basix)**: basic data structures and functions I keep reaching for, 
    including stacks, queues (with concurrent variants) and stream `Gatherer`s.
- **[xmls](https://github.com/ralfspoeth/xmls)**: the W3C DOM through `java.util.stream`, for navigating, 
    filtering and extracting typed values from XML. Its API is settled at 1.0.
- **[utf8](https://github.com/ralfspoeth/utf8)**: fast `Reader` and `Writer` implementations for UTF-8, 
    built on Björn Höhrmann's branchless DFA decoder.
- **[filews](https://github.com/ralfspoeth/filews)**: a small callback-based wrapper around the JDK 
    `WatchService`, running on virtual threads.

## Every Library Ships a `module-info.java`

Being a kind citizen, mostly. Writing a `module-info.java` costs the author
something (the test path gets awkward, split packages are out, reflection needs
`opens`), and almost all of the benefit lands on whoever consumes the library.

Without one, a modular consumer has to take the jar as an automatic module, named
by guessing from the filename, and cannot `jlink` a runtime image that includes
it. The library becomes the reason somebody else can't be strict. With one, they
get a stable name, a dependency graph the compiler checks before anything runs,
and services declared rather than configured.

It is also the only way to say which packages are *not* API. Internals stay
unexported and so remain free to change. That part is a kindness to the author
too, but it's the enforcement that makes the promise worth anything.
