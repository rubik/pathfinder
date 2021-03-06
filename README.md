# pathfinder

A utility to find file paths.

## Documentation

In depth documentation is available on [Read the Docs](https://pathfinder.readthedocs.org/en/latest/)

## Examples

    from pathfinder import find

    # get all directories and sub-directories in current directory
    paths = find(".", just_dirs=True)

    # get all files in the current directory and all sub-directories
    paths = find(".", just_files=True)

    # get all jpg files using a regex
    paths = find(".", regex=".*\.jpg$")

    # get all jpg files using posix wildcards
    paths = find(".", fnmatch="*.jpg")

    # get all jpg files and png files
    from pathfinder import FnmatchFilter
    from pathfinder import OrFilter
    jpg_filter = FnmatchFilter("*.jpg")
    png_filter = FnmatchFilter("*.png")
    gif_filter = FnmatchFilter("*.gif")
    image_filter = OrFilter(jpg_filter, png_filter, gif_filter)
    paths = find(".", filter=image_filter)

    # shortcut using bitwise or
    paths = find(".", filter=jpg_filter | png_filter | gif_filter)

    # even shorter using ImageFilter to find all images
    from pathfinder import ImageFilter
    paths = find(".", filter=ImageFilter())

    # and an even shorter way
    paths = ImageFilter().find(".")

## Build Status

[![Build Status](https://travis-ci.org/jkeyes/pathfinder.png?branch=pillow-dev)](https://travis-ci.org/jkeyes/pathfinder)