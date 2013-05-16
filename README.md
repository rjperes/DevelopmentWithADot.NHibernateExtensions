DevelopmentWithADot.NHibernateExtensions
===============================================

NHibernate extensions.
Discussed on http://weblogs.asp.net/ricardoperes/archive/2013/02/15/nhibernate-extensibility.aspx.

DateTime extension methods (for Query Over):
- Int32 Day(this DateTime dateTimeProperty): returns the day part of a date
- Int32 Month(this DateTime dateTimeProperty): returns the month part of a date
- Int32 Year(this DateTime dateTimeProperty): returns the year part of a date

Dialect extension methods:
- Dialect GetDialect(this ISessionFactory factory): returns the current Dialect from a session factory
- ISQLFunction RegisterFunction<T>(this ISessionFactory factory, String name): registers a new SQL function that exists on the database
- ISQLFunction RegisterFunction<T>(this ISessionFactory factory, String name, String sql): registers a new SQL function with custom SQL

IEnumerable<TSource> extension methods:
- IQueryable<T> Query<T>(this IEnumerable<T> collection): executes a server-side query over an entity collection

ISession extension methods:
- T Attach<T>(this ISession session, T entity, LockMode mode = null): attaches a disconnected entity to a session
- Int32 Delete<T>(this ISession session): deletes all entities of a given type
- Boolean DeleteById<T>(this ISession session, Object id): deletes a single entity by its id
- EntityEntry Entry<T>(this ISession session, T entity): returns the First Level Cache entry for a given entity
- void Evict<T>(this ISession session): removes all entities of a given type from the First Level Cache
- void Evict<T>(this ISession session, Object id): removes a single of a given type from the First Level Cache by its id
- IDictionary<String, Object> GetDirtyProperties<T>(this ISession session, T entity): returns all the dirty properties of an entity
- T GetFromCache<T>(this ISession session, Object id): returns an entity of a given type from the First Level Cache by its id
- Boolean HasDirtyProperties(this ISession session, Object entity): checks if an entity has dirty properties
- IEnumerable<T> Local<T>(this ISession session, Status status = Status.Loaded): returns all of the entities of a given type from the First Level Cache
- IQueryable Query(this ISession session, Type entityType): returns a not strongly typed query for a given entity
- void Reset(this ISession session, Object entity): resets an entity to its original definition

IQueryable<TSource> extension methods (for LINQ):
- IQueryable<TSource> Between<TSource, TKey>(this IQueryable<TSource> source, Expression<Func<TSource, TKey>> keySelector, TKey low, TKey high) where TKey : IComparable<TKey>: returns all entities whose property is between two boundary values
- IQueryable<TSource> Compare<TSource>(this IQueryable<TSource> query, Operand op, String propertyName, Object value = null): returns all entities that match a condition
- IOrderedQueryable<TSource> OrderBy<TSource>(this IQueryable<TSource> query, String propertyName): orders a previously unordered query by a property name as a string
- IOrderedQueryable<TSource> OrderBy<TSource>(this IQueryable<TSource> query, String propertyName, Boolean ascending): orders a previously unordered query by a property name as a string and a flag
- IOrderedQueryable<TSource> OrderByDescending<TSource>(this IQueryable<TSource> query, String propertyName): orders descending a previously unordered query by a property name as a string
- IOrderedQueryable<TSource> ThenBy<TSource>(this IOrderedQueryable<TSource> query, String propertyName): orders an already ordered query by a property name as a string
- IOrderedQueryable<TSource> ThenBy<TSource>(this IQueryable<TSource> query, String propertyName, Boolean ascending): orders an already ordered query by a property name as a string and a flag
- IOrderedQueryable<TSource> ThenByDescending<TSource>(this IOrderedQueryable<TSource> query, String propertyName): orders descending an already ordered query by a property name as a string

String extension methods (for LINQ):
- String Soundex(this String input): applies the SOUNDEX algorithm to a string (SQL Server only)

Copyright Ricardo Peres 2013