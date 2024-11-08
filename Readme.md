<!-- To create new DB -->
CREATE DATABASE ecommerce;

<!-- To switch DB -->
USE ecommerce;

<!-- Creating Customer table -->
CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    address VARCHAR(255)
);

<!-- Creating Products table -->
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price DECIMAL(10, 2) NOT NULL,
    description TEXT
);

<!-- Creating Orders table -->
CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

<!-- Inserting random entries for customer table -->
INSERT INTO customers (name, email, address) VALUES
('John Doe', 'john.doe@example.com', '123 Elm Street'),
('Jane Smith', 'jane.smith@example.com', '456 Oak Street'),
('Mike Johnson', 'mike.johnson@example.com', '789 Pine Street'),
('Emily Davis', 'emily.davis@example.com', '321 Maple Street'),
('Sarah Brown', 'sarah.brown@example.com', '654 Cedar Street'),
('Chris Lee', 'chris.lee@example.com', '987 Birch Street'),
('Katie Wilson', 'katie.wilson@example.com', '258 Spruce Street'),
('David Miller', 'david.miller@example.com', '369 Aspen Avenue'),
('Laura Garcia', 'laura.garcia@example.com', '741 Walnut Lane'),
('James Martinez', 'james.martinez@example.com', '852 Cherry Road'),
('Mia Anderson', 'mia.anderson@example.com', '135 Sycamore Drive'),
('Robert Clark', 'robert.clark@example.com', '246 Dogwood Place'),
('Linda Wright', 'linda.wright@example.com', '357 Alder Court'),
('Tom Hall', 'tom.hall@example.com', '468 Cypress Avenue'),
('Sophia Scott', 'sophia.scott@example.com', '579 Beech Street'),
('Daniel Young', 'daniel.young@example.com', '680 Redwood Road'),
('Grace Adams', 'grace.adams@example.com', '791 Cedar Lane'),
('Paul Walker', 'paul.walker@example.com', '802 Maple Street'),
('Ella King', 'ella.king@example.com', '913 Elm Street'),
('Ryan Turner', 'ryan.turner@example.com', '102 Oak Avenue'),
('Olivia Lopez', 'olivia.lopez@example.com', '113 Pine Road'),
('Benjamin Perez', 'benjamin.perez@example.com', '124 Maple Drive'),
('Victoria Rivera', 'victoria.rivera@example.com', '135 Birch Lane'),
('Jack Baker', 'jack.baker@example.com', '146 Spruce Avenue'),
('Chloe Nelson', 'chloe.nelson@example.com', '157 Redwood Drive'),
('Lucas Carter', 'lucas.carter@example.com', '168 Cherry Court'),
('Ella Foster', 'ella.foster@example.com', '179 Aspen Road'),
('Henry Ramirez', 'henry.ramirez@example.com', '190 Dogwood Lane'),
('Grace Bell', 'grace.bell@example.com', '201 Cypress Avenue'),
('Mason Diaz', 'mason.diaz@example.com', '212 Oak Court'),
('Isabella Hayes', 'isabella.hayes@example.com', '223 Pine Lane'),
('Liam Brooks', 'liam.brooks@example.com', '234 Maple Drive'),
('Zoe James', 'zoe.james@example.com', '245 Elm Street'),
('Ethan Sanders', 'ethan.sanders@example.com', '256 Beech Road'),
('Amelia Green', 'amelia.green@example.com', '267 Cedar Lane'),
('William Moore', 'william.moore@example.com', '278 Sycamore Avenue'),
('Emma Hughes', 'emma.hughes@example.com', '289 Alder Drive'),
('Lucas Kelly', 'lucas.kelly@example.com', '300 Cherry Street'),
('Ava Collins', 'ava.collins@example.com', '311 Spruce Road'),
('Noah Butler', 'noah.butler@example.com', '322 Redwood Lane');


<!-- Inserting random data for produccts table -->
INSERT INTO products (name, price, description) VALUES
('Product A', 1200.00, 'High-performance laptop with 16GB RAM and 512GB SSD.'),
('Product B', 699.99, 'Latest model with 5G support and 128GB storage.'),
('Product C', 99.99, 'Wireless over-ear headphones with noise cancellation.');



<!-- Inserting random data for orders table -->
INSERT INTO orders (customer_id, order_date, total_amount) VALUES
(1, '2024-10-01', 99.99),
(2, '2024-10-02', 150.00),
(3, '2024-10-03', 699.99),
(4, '2024-10-04', 250.00),
(5, '2024-10-05', 1200.00),
(6, '2024-10-06', 550.75),
(7, '2024-10-07', 49.99),
(8, '2024-10-08', 350.50),
(9, '2024-10-09', 250.00),
(10, '2024-10-10', 199.95),
(11, '2024-10-11', 500.00),
(12, '2024-10-12', 45.00),
(13, '2024-10-13', 25.99),
(14, '2024-10-14', 135.50),
(15, '2024-10-15', 85.75),
(16, '2024-10-16', 35.00),
(17, '2024-10-17', 150.00),
(18, '2024-10-18', 249.99),
(19, '2024-10-19', 74.99),
(20, '2024-10-20', 129.50),
(21, '2024-10-21', 79.95),
(22, '2024-10-22', 110.00),
(23, '2024-10-23', 210.75),
(24, '2024-10-24', 599.99),
(25, '2024-10-25', 49.99),
(26, '2024-10-26', 325.50),
(27, '2024-10-27', 100.00),
(28, '2024-10-28', 19.99),
(29, '2024-10-29', 45.50),
(30, '2024-10-30', 399.99),
(31, '2024-10-31', 250.75),
(32, '2024-11-01', 249.99),
(33, '2024-11-02', 30.00),
(34, '2024-11-03', 210.00),
(35, '2024-11-04', 89.95),
(36, '2024-11-05', 140.00),
(37, '2024-11-06', 550.00),
(38, '2024-11-07', 75.99),
(39, '2024-11-08', 129.99),
(40, '2024-11-09', 59.95);

<!-- To Retrieve all customers who have placed an order in the last 30 days. -->
SELECT customers.*
FROM customers
RIGHT JOIN orders ON customers.id = orders.customer_id
WHERE orders.order_date >= CURDATE() - INTERVAL 30 DAY
GROUP BY customers.id;


<!-- To Get the total amount of all orders placed by each customer. -->
SELECT customers.id, customers.name, SUM(orders.total_amount) AS total_spent
FROM customers
JOIN orders ON customers.id = orders.customer_id
GROUP BY customers.id;


<!-- To Update the price of Product C to 45.00. -->
UPDATE products 
SET price = 45.00 
WHERE name = 'Product C';


<!-- To Add a new column discount to the products table. -->
ALTER TABLE products
ADD discount DECIMAL(5, 2);


<!-- To Retrieve the top 3 products with the highest price. -->
SELECT * 
FROM products
ORDER BY price DESC
LIMIT 3;


<!-- To Get the names of customers who have ordered Product A. -->
SELECT DISTINCT customers.name
FROM customers
JOIN orders ON customers.id = orders.customer_id
JOIN products ON orders.product_id = products.id
WHERE products.name = 'Product A';


<!-- To Join the orders and customers tables to retrieve the customer's name and order date for each order.  -->
SELECT customers.name, orders.order_date
FROM orders
JOIN customers ON orders.customer_id = customers.id;


<!-- To Retrieve the orders with a total amount greater than 150.00. -->
SELECT *
FROM orders
WHERE total_amount > 150.00;


<!-- To Normalize the database by creating a separate table for order items and updating the orders table to reference the order_items table. -->
<!-- Create a new table -->
CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY, 
    order_id INT,                          
    product_id INT,                       
    quantity INT DEFAULT 1,                
    FOREIGN KEY (order_id) REFERENCES orders(id), 
    FOREIGN KEY (product_id) REFERENCES products(id) 
);

<!-- Insert values -->
INSERT INTO order_items (order_id, product_id, quantity)
VALUES (1, 2, 1), 
       (1, 3, 2),
       (2, 1, 1);

<!-- Join the tables to get data -->
SELECT orders.id AS order_id, orders.order_date, orders.product_id AS main_product_id, products.name AS product_name, order_items.quantity
FROM orders
LEFT JOIN order_items ON orders.id = order_items.order_id
LEFT JOIN products ON order_items.product_id = products.id;

<!-- To Retrieve the average total of all orders. -->
SELECT AVG(total_amount) AS average_order_total
FROM orders;