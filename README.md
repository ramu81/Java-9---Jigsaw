# Java-9---Jigsaw
src\com.world\module-info.java
src\com.world\com\chinna\kadira\World.java
src\edu.kondapalli\edu\greetings\Greetings.java
src\edu.kondapalli\module-info.java

mkdir src\com.world\com\chinna\kadira src\edu.kondapalli\edu\greetings 

start notepad module-info.java

	module com.world {
        exports com.chinna.kadira;
    }
	
start notepad World.java
	
	package com.chinna.kadira;
    public class World {
        public static String name() {
            return "world";
        }
    }
	
start notepad module-info.java

	module edu.kondapalli {
        requires com.world;
    }

start notepad Greetings.java

    package edu.greetings;
    import com.chinna.kadira.World;
    public class Greetings {
        public static void main(String[] args) {
            System.out.format("Greetings %s!%n", World.name());
        }
    }
	
javac -d mods\com.world src\com.world\module-info.java src\com.world\com\chinna\kadira\World.java

javac --module-path mods -d mods\edu.kondapalli src\edu.kondapalli\module-info.java src\edu.kondapalli\edu\greetings\Greetings.java

java --module-path mods -m edu.kondapalli/edu.greetings.Greetings
