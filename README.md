# Course category upload (tool_uploadcoursecategory)

An admin tool for creating, updating, renaming and deleting course categories
in bulk from a CSV file, in the same way that **Upload users** works for users.

After installing, go to **Site administration → Courses → Upload course
categories**.

## Requirements

- Moodle 5.1 to 5.3 LTS
- PHP 8.2 or later (Moodle 5.2 and 5.3 need PHP 8.3 or later)
- Capability `moodle/category:manage` in the system context

## Installing via uploaded ZIP file

1. Log in to your Moodle site as an admin and go to
   **Site administration → Plugins → Install plugins**.
2. Upload the ZIP file. The folder inside the ZIP must be called
   `uploadcoursecategory`. If it isn't, use **Show more… → Rename the root
   directory** and enter `uploadcoursecategory`.
3. Check the plugin validation report and finish the installation.

## Installing manually

Copy the plugin folder to:

    {your/moodle/dirroot}/public/admin/tool/uploadcoursecategory

(Moodle 5.1 and later keep plugins under `public/`.)

Then log in as an admin and go to **Site administration → Notifications** to
finish the installation, or run:

    php admin/cli/upgrade.php

## CSV file format

Allowed column names: `name`, `description`, `idnumber`, `theme`, `visible`,
`deleted` (1 means delete the category) and `oldname` (for renaming).

Example file for adding categories:

    name,idnumber,description
    EveryThing,EveryThing,EveryThing
    EveryThing/Board_of_Trustees,Board_of_Trustees,Board_of_Trustees
    EveryThing/Teachers,Teachers,Teachers
    EveryThing/Teachers/TeachingStaff,TeachingStaff,TeachingStaff
    EveryThing/Teachers/NonTeachingStaff,NonTeachingStaff,NonTeachingStaff

Example file for deleting a category (choose the upload type
**Update existing Course categories only** and set **Allow deletes** to Yes):

    name,deleted
    EveryThing,1

**Be extremely careful with deletion: it deletes the category and everything
in it, including all of its courses and sub-categories.**

### Category names

Give the category name exactly as it appears in Moodle; it is case sensitive.
For sub-categories, give the full path separated by `/`, for example
`Miscellaneous/Sub Cat/Sub Sub Cat`. Parent categories must already exist, or
appear on an earlier line of the same file.

## Credits

Originally written by Piers Harding (2012), based on Moodle's Upload users
tool by Petr Skoda and others. Maintained by Vernon Spain.

## License

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later
version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program. If not, see <https://www.gnu.org/licenses/>. The full text is in
the `LICENSE` file.
