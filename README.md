# waterline-sequel-snowflake

Waterline sql translator for Snowflake, for use with snowflake-waterline-adapter.

Snowflake-specific changes:

 - Expects a criteriaWrapper value in the adapter. If there is no criteriaWrapper set, it defaults to single quotes. Snowflake barfs on double quotes and ticks in the query where clause values, and the base waterline-sequel package defaults to hard-coded double quotes. The CriteriaProcessor uses the criteriaWrapper value in a new utility method that returns the appropriately wrapped value.

 - the escapeCharacter, passed in from the adapter and set as double quotes by default, can't be a tick, used by mysql. Snowflake sees that tick and gets a rash, not the good kind.
